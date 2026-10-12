# Data collection and preprocessing

[Project](../README.md) · [한국어](README.ko.md) · [Data design](../docs/wiki/Data.md)

Historical scripts for Ohouse interior posts, products, photographs and their relationships. Check current terms and access policies before collecting data; this documentation is not scraping permission.

## Options and execution

- `--just_update`: collect unseen data only; without it, collect all data.
- `--target`: targets from `housecode`, `hi`, `hc`, `house`, `item`, `card`, `color`.

From `crawling/`:

```bash
python main.py
python main.py --just_update
python main.py --just_update --target housecode hi hc house item card
```

The last example skips color updates. Run `housecode` before `hi`/`hc`/`house`, `hi` before `item`, and `hc` before `card`. Color collection is independent.

## Layout

`args.py` and `config.py` configure collection; `main.py`, `crawling_modules.py` and `utils.py` implement it. `preprocess.py` cleans and integrates data. Local `data/` contains per-post and merged CSVs, including `hi_interaction.csv`, `hc_interaction.csv`, `house.csv`, `item.csv`, `card.csv` and color tables.

## Historical troubleshooting

- Pandas/tqdm `AttributeError: 'Series' object has no attribute '_is_builtin_func'`: original workaround `pip install tqdm==4.62.2`.
- KoNLPy `JVMNotFoundException`: install a suitable JDK and configure `JAVA_HOME`. See the [macOS issue](https://github.com/konlpy/konlpy/issues/353).

Original preprocessing smoke test:

```bash
python preprocess.py --data_path data/ --test 1
```

These notes reflect 2023 dependencies, not guaranteed compatibility with the current site.
