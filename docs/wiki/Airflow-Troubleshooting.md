# Airflow troubleshooting

## DAG files do not appear in the web UI

Two hypotheses were considered:

### File scanning is too slow

The team's notes recorded `min_file_process_interval=300` in `airflow.cfg`. A five-minute interval can make changes look missing. Reducing it to **30** improved feedback speed, but lower intervals consume resources; tune rather than minimizing indiscriminately.

### The base directory is wrong

In the author's case, neither editing configuration nor reinitializing the database seemed to take effect. Setting `AIRFLOW_HOME` to an **absolute path** resolved the problem.

To hide bundled examples, set `load_examples = False`. If changes are not reflected, recheck the configured base directory and the historical initialization steps.

The recorded example directory was `/opt/ml/input/airflow_practice`.

## Timezone error

A shell setting in the form `KST-09:00:00` caused Airflow's `TimezoneNotFound` error. The author resolved it by using the named timezone:

```bash
export TZ='Asia/Seoul'
```


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Airflow-%EC%97%90%EB%9F%AC-%ED%95%B4%EA%B2%B0)
