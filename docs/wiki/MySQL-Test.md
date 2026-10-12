# Local MySQL test

The original example uses `pymysql` to connect to port **3306** and execute SQL for database/table creation, insertion and selection. Install `pymysql` in your environment first.

```python
# import library
import pymysql

# connect to db and make cursor
conn = pymysql.connect(host='127.0.0.1', user='root', password='1234', port=3306, charset='utf8')
cur = conn.cursor()

# sql queries
create_db = "CREATE DATABASE IF NOT EXISTS project_db;"
use_db = "USE project_db;"
create_table = "CREATE TABLE IF NOT EXISTS member_tmp\
                (user_id CHAR(100) NOT NULL PRIMARY KEY);"
insert_data = "INSERT INTO member_tmp VALUES\
                ('유영서'),\
                ('Boost Camp AI Tech 4th'),\
                ('asdfasdfadsfasdfasdfasdfa'),\
                ('_123dafdEAFDF@#$%;'),\
                ('/;\/;\/;\/;\/;\/;\');"
select_data = "SELECT * FROM member_tmp;"

# excute
cur.execute(create_db)
cur.execute(use_db)
cur.execute(create_table)
cur.execute(insert_data)
cur.execute(select_data)
conn.commit() # save execution
conn.close() # close db connection

# print selected data from database
data = cur.fetchall() # fetchone(), fetchmany(size: int)
for id in data:
    print(f"Member id: {id[0]}")
```

**Historical example, not production guidance:** The snippet retains its original local test password and Korean test string for fidelity. Replace credentials with your own secure local configuration. It also fetches results after closing the connection; inspect resource ordering before reuse. The example is preserved, not presented as a tested modern implementation.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/MySQL-%ED%85%8C%EC%8A%A4%ED%8A%B8)
