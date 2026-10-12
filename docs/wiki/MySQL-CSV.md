# Importing CSV into MySQL

Original import statement:

```sql
LOAD DATA LOCAL INFILE "FILE_PATH" INTO TABLE DBNAME.TABLE_NAME FIELDS TERMINATED BY ",";
```

## Error: local loading disabled

`ERROR 3948 (42000): Loading local data is disabled; this must be enabled on both the client and server sides`

Check the setting:

```sql
mysql> show global variables like 'local_infile';
```

<img src = "https://user-images.githubusercontent.com/90206705/217549014-acf0b795-2d42-47e5-907e-143e475592dc.png" width=40% height=20%)>

The original workaround enabled the server setting:

```sql
mysql> set global local_infile=true;
```

<img src = "https://user-images.githubusercontent.com/90206705/217549194-f3d1fb92-2dc4-44ad-a095-0ea0b02a3345.png" width=40% height=20%>

Reconnect after changing it and retry the import, ensuring the client also permits local loading.

**Safety note:** Enable local file loading only in an appropriately trusted environment. This historical workaround is not a recommendation to weaken a shared database's policy.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/MySQL-csv-%EB%84%A3%EA%B8%B0)
