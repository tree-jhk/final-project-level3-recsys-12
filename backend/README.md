# Backend — FastAPI

[Project](../README.md) · [한국어](README.ko.md) · [API reference](../docs/wiki/API.md)

<p align="center"><img src="https://cdn-images-1.medium.com/fit/t/1600/480/1*du7p50wS_fIsaC_lR18qsg.png"></p>

The backend connects the web interface to user/item services, MySQL and recommendation inference.

## Layout

- `main.py`, `__main__.py`: application/server entry points.
- `service/`: user and item services.
- `db/`: database connection and models.
- `inference/`: recommendation and signup inference.
- `pyproject.toml`, `poetry.lock`: dependencies.

## Historical setup

Install Poetry following its [official instructions](https://python-poetry.org/docs/), then run from the repository root:

```bash
cd backend
poetry install
poetry run python __main__.py
```

The original Ubuntu setup also installed curl. Install system packages only with appropriate permissions. Data, checkpoints and private configuration are not supplied. See [database](../database/README.md), [GCP](../gcp/README.md) and [CORS](../docs/wiki/CORS.md).
