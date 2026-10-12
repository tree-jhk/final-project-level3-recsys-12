# Database manager — MySQL

[Project](../README.md) · [한국어](README.ko.md) · [Database wiki](../docs/wiki/Database.md)

`db_manager.py` manages the schema through `sql/`. Local `data/` holds input/output CSVs; datasets and credentials are not bundled.

## Setup

Install dependencies from `requirements.txt`. Configure the repository-root `secrets.yaml` locally; never commit it:

```yaml
DB:
  user: YOUR_DB_USER
  password: YOUR_DB_PASSWORD
  host: YOUR_DB_HOST
  port: 3306
  database: YOUR_DB_NAME
```

From `database/`:

```bash
python db_manager.py --command create
```

`python db_manager.py --command delete` **deletes tables**; use only intentionally against a confirmed disposable database.

See [ERD](../docs/wiki/ERD.md), [CSV import](../docs/wiki/MySQL-CSV.md) and the historical [security incident](../docs/wiki/Security-Incident.md).
