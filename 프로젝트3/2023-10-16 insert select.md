db 인서트 자동시퀀스 
### insert code
```PYTHON
from flask import Flask, request, jsonify  
import cx_Oracle  
  
# 오라클 클라이언트 라이브러리 초기화  
cx_Oracle.init_oracle_client(lib_dir=r"C:\oraclexe\app\instantclient_19_20")  
  
app = Flask(__name__)  
  
# Oracle 데이터베이스 연결 정보  
username = 'DCLTEST'  
password = '12345'  
dsn = 'xe'  # 실제 TNS 이름으로 변경  
  
  
@app.route('/')  
def hello_world():  
    return 'Hello, World!'  
  
  
@app.route('/query')  
def query_database():  
    try:  
  
        # Oracle 데이터베이스에 연결  
        connection = cx_Oracle.connect(username, password, dsn)  
        cursor = connection.cursor()  
  
        # if문 셀렉트해서 기존의 url 데이터가 있는지 조회  
        # sql = "UPDATE T_URL SET LEAD_CNT = LEAD_CNT + 1 WHERE URL_SEQ = 1" # 조회수 +1 sql문  
        # else : (db에 정보 없다면 주석풀고 여기서 밑에서 실행)  
        # 실행할 SQL 쿼리 (테이블 이름은 실제 데이터베이스에 맞게 수정해야 함)  
        sql_query = """  
            INSERT INTO T_URL (URL_SEQ, URL_NAME, MLCS_STTS, URL_YN, URL_CNT, URL_DATE)VALUES (URL_SEQ.NEXTVAL, 'example.com', 'Y', 'Y', 1, TIMESTAMP '2023-10-13 12:00:00.000000')  
        """  
        cursor.execute(sql_query)  
  
        connection.commit()  
  
        # 커서와 연결 닫기  
        cursor.close()  
        connection.close()  
  
        response = {'message': 'Data inserted successfully'}  
        return jsonify(response)  
  
  
  
  
  
  
        # return jsonify(response)  
        # 결과 가져오기  
        # results = cursor.fetchall()  
        # connection.commit  
        # 결과를 JSON 형식으로 반환  
        #response = [{'column1': row[0]} for row in results]  
  
    except cx_Oracle.Error as error:  
        return jsonify({'error': str(error)})  
  
  
if __name__ == '__main__':  
    app.run()
```

---

### 시퀀스 초기화
```
-- 시퀀스 삭제
DROP SEQUENCE INC_URL_SEQ;

-- 새로운 시퀀스 생성
CREATE SEQUENCE INC_URL_SEQ
       INCREMENT BY 1
       START WITH 1
       MINVALUE 1
       MAXVALUE 1000000
       NOCYCLE
       NOCACHE
       ORDER;
```


- 이미 데이터베이스에 저장된 데이터가 이전 시퀀스 값을 가지고 있을 수 있다는 것입니다. 데이터베이스 내의 모든 테이블에서 이전 시퀀스 값을 갖고 있는 데이터는 변경되지 않으며, 새로운 데이터만 새로운 시퀀스 값을 사용합니다.

---

