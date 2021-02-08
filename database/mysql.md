## mysql

- 루트 말고 로컬 아이디 접속법 `mysql -u python -p` -> 비밀번호 입력 `-u` - 계정명, `-p`- 패스워드
- `show databases;`
- `use <db명>;`
- `show tables;`
- `desc <table 명>;` : 간단하게 테이블 정보 표현
- 끝에 **콜론** 잊지 말기



- mariaDB는 mysql의 발전된 대체제, sqlite는 mariaDB와 다른 편



- 파이썬에서...
  - 데이터 베이스와 연결 : pymysql
  - 객체를 rdb와 mapping 쉽게 해줌 : sqlalchemy



```python
import pymysql
import sqlalchemy

#pymysql과 sqlalchemy 연동
pymysql.install_as_MySQLdb()
from sqlalchemy import create_engine

engine = create_engine('mysql+mysqldb://python:python@localhost:3306/python_db', encoding='utf-8')
print(engine)
#engine을 통해 db에 연결
con = engine.connect()
print(con)

#DataFrame to_sql() 함수로 dataframe객체를 table로 저장
song_df.to_sql(name ='테이블이름', con =engine, index=False, if_exists ='replace')
```



```python
#pymysql만 사용시

sql = """
CREATE TABLE product (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name VARCHAR(20) NOT NULL,
    model_num VARCHAR(10) NOT NULL,
    model_type VARCHAR(10) NOT NULL,
    PRIMARY KEY(id)
);
"""

import pymysql

db = pymysql.connect(host='localhost', port=3306, db='python_db',\
                    user='python',passwd='python',charset='utf8')
cursor = db.cursor()
cursor.execute(sql)
db.commit()
```

