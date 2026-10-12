# Airflow environment setup

Historical notes extending the team's course material; version **2.2.0** was used.

## Environment

```bash
conda create -n airflow python=3.8.5
pip install 'apache-airflow==2.2.0'
```

## Set the base directory

Use an **absolute path** for `AIRFLOW_HOME`. The team found that the AI Stages server sometimes lost the setting, so it recorded the export in `.bashrc`.

```bash
export AIRFLOW_HOME=/absolute/path/to/airflow
```

## Initialize the database

From the configured directory, run the historical `airflow db init` command.

## Administrator account

![Untitled](https://user-images.githubusercontent.com/90206705/217561916-3e22b9d2-118c-45d2-873e-fd55a2a5bf37.png)

Include all required fields when creating the account. The command may be written on one line rather than using continuation backslashes.

## Start webserver and scheduler

Run `airflow webserver --port 8080`. In a **separate terminal**, activate the Airflow environment, set/verify the base directory and run `airflow scheduler`.

If DAG changes appear to have no effect, check that the scheduler is running and the DAG is enabled. Commands here describe the project's old environment; do not assume they are the current Airflow setup procedure.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Airflow-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95)
