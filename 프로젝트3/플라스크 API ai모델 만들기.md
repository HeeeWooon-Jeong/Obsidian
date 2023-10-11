

# 흐름도 코드
```python
## 클라이언트가 요청한 정보를 먼저 DB와 대조하고, DB에 해당 정보가 없으면 머신러닝 모델을 사용하여 결과를 생성하고 DB에 저장하는 코드를 작성할 것입니다. 아래는 이러한 작업을 수행하는 Flask 애플리케이션 코드의 예시입니다.  
  
import cx_Oracle  
from pydantic import BaseModel  
from flask import Flask, request, jsonify  
from sklearn.linear_model import LinearRegression  # 머신러닝 모델 예시  
  
# Flask 애플리케이션 생성  
app = Flask(__name__)  
  
# Oracle DB 연결 정보 설정  
db_username = 'DCLTEST'      # 수정
db_password = '12345'        # 수정
db_dsn = 'xe'  # DSN (Data Source Name) 설정  
  
# 모델 정의 (머신러닝 모델 예시)  
class Model(BaseModel):  
    url: str  
  
# 머신러닝 모델 초기화  
ml_model = LinearRegression()  # 머신러닝 모델을 여기에 초기화하십시오.  
  
# URL에서 데이터를 받아 Oracle DB에서 데이터 조회 또는 머신러닝 모델 사용  
@app.route('/url', methods=['POST'])  
def ML():  
    data = request.get_json()  # JSON 데이터를 받아옵니다.  
  
    # Oracle DB 연결  
    connection = cx_Oracle.connect(user=db_username, 
    password = db_password, dsn=db_dsn)  
  
    # 커서 생성  
    cursor = connection.cursor()  
  
    try:  
        # SQL 쿼리 실행  
        sql = "SELECT column_name FROM [테이블이름] WHERE url = :url"  
        cursor.execute(sql, url=data['url'])  
  
        # DB에서 결과 가져오기  
        db_result = cursor.fetchone()  
  
        if db_result:  
            # DB에 데이터가 있는 경우 DB 결과를 리턴  
            return jsonify({'result': db_result[0]})  
        else:  
            # DB에 데이터가 없는 경우 머신러닝 모델을 사용하여 결과 생성  
            # 여기에서 머신러닝 모델을 사용하여 결과를 생성하는 코드를 작성하세요.  
            # 결과를 생성하고 DB에 저장하려면 DB 삽입 쿼리를 실행하세요.  
  
            # 머신러닝 모델을 사용한 결과 (예시)  
            ml_result = ml_model.predict([[data['url']]])[0]  
  
            # DB에 결과 저장 (예시)  
            insert_sql = "INSERT INTO your_table (url, result) VALUES (:url, :result)"  
            cursor.execute(insert_sql, url=data['url'], result=ml_result)  
            connection.commit()  
  
            # 결과값 리턴  
            return jsonify({'result': ml_result})  
  
    finally:  
        # 커서와 연결 닫기  
        cursor.close()  
        connection.close()  
  
if __name__ == '__main__':  
    app.run(host='0.0.0.0', port=8000)
```


# 플라스크 API ai 모델 만들기
AI 모델을 API로 노출하기 위해 Flask를 사용하는 것은 일반적인 작업입니다. 아래는 Flask를 사용하여 AI 모델 API를 만드는 기본 단계입니다.

1. **Flask 설치:** 먼저 Flask를 설치해야 합니다. 터미널에서 다음 명령을 실행하여 Flask를 설치합니다.

   ```
   pip install Flask
   ```

2. **Flask 애플리케이션 생성:** Python 스크립트를 만들고 Flask 애플리케이션을 생성합니다.

   ```python
   from flask import Flask, request, jsonify

   app = Flask(__name__)
   ```

3. **AI 모델 불러오기:** AI 모델을 불러옵니다. 모델을 불러오는 방법은 모델의 종류 및 사용하는 라이브러리에 따라 다릅니다. TensorFlow, PyTorch, Scikit-Learn 등의 라이브러리를 사용할 수 있습니다.

4. **API 엔드포인트 정의:** Flask를 사용하여 모델에 접근할 수 있는 API 엔드포인트 를 정의합니다. 예를 들어, 모델을 사용하여 이미지 분류를 수행하는 엔드포인트를 만들 수 있습니다.

   ```python
   @app.route('/classify', methods=['POST'])
   def classify_image():
       # 클라이언트로부터 이미지를 받아옴
       image_data = request.files['image'].read()

       # 이미지 분류 모델을 사용하여 예측
       prediction = your_model_function(image_data)

       # 예측 결과를 JSON 형태로 반환
       return jsonify({'prediction': prediction})
   ```

5. **모델 함수 작성:** 모델 함수를 작성하여 클라이언트의 요청에 따라 모델을 실행하고 결과를 반환합니다.

6. **서버 실행:** Flask 애플리케이션을 실행합니다.

   ```python
   if __name__ == '__main__':
       app.run(host='0.0.0.0', port=5000)
   ```

7. **API 사용:** Flask 애플리케이션이 실행 중일 때, 클라이언트는 API에 POST 요청을 보내고 모델의 결과를 받을 수 있습니다.

   예를 들어, Python의 requests 라이브러리를 사용하여 API를 호출할 수 있습니다.

   ```python
   import requests

   image_file = open('test_image.jpg', 'rb')
   files = {'image': image_file}
   response = requests.post('http://localhost:5000/classify', files=files)
   result = response.json()
   ```

8. **보안 및 오류 처리:** API 보안을 강화하고 오류 처리를 구현하여 안정성을 높이세요. 또한, 모델 예측 시 예외 처리를 고려하세요.

9. **API 문서화 및 테스트:** API의 사용법을 문서화하고 테스트하여 개발자 및 사용자가 쉽게 이해하고 사용할 수 있도록 합니다.

이제 이러한 단계를 따라 Flask를 사용하여 AI 모델 API를 만들 수 있습니다. AI 모델의 종류와 기능에 따라 엔드포인트와 모델 함수를 적절하게 구성하세요.

---
# 엔드포인트 
>  API 엔드포인트(API Endpoint)는 웹 API(웹 애플리케이션 프로그래밍 인터페이스)를 통해 클라이언트가 서버와 상호작용할 수 있는 특정한 URL(Uniform Resource Locator) 또는 URI(Uniform Resource Identifier)를 나타냅니다. 간단히 말해, API 엔드포인트는 웹 서비스에서 특정 기능 또는 데이터에 접근하기 위한 주소 또는 경로입니다.

API 엔드포인트는 일반적으로 HTTP 요청을 통해 접근되며, 다음과 같은 기본적인 HTTP 메서드를 사용하여 상호 작용합니다:

1. **GET** : 정보를 요청하거나 데이터를 검색하는 데 사용됩니다. 주로 데이터를 가져오는 데 사용됩니다.

2. **POST**: 새로운 데이터를 생성하거나 업데이트하는 데 사용됩니다. 주로 데이터를 전송하여 서버에 저장하는 데 사용됩니다.

3. **PUT**: 특정 리소스를 업데이트하는 데 사용됩니다. 전체 리소스를 대체하는 데 주로 사용됩니다.

4. **DELETE**: 특정 리소스를 삭제하는 데 사용됩니다.

API 엔드포인트는 클라이언트와 서버 간의 통신을 효과적으로 관리하고 특정 작업을 수행하기 위해 사용됩니다. 예를 들어, 웹 애플리케이션에서 데이터베이스에서 데이터를 읽거나 쓰기, 외부 서비스와 통신하는 등의 작업을 수행하는 데 API 엔드포인트를 활용할 수 있습니다.

예를 들어, 다음은 간단한 RESTful API의 엔드포인트 예시입니다:

- `GET /api/users`: 사용자 목록을 가져오는 엔드포인트.
- `POST /api/users`: 새로운 사용자를 생성하는 엔드포인트.
- `PUT /api/users/{id}`: 특정 사용자의 정보를 업데이트하는 엔드포인트.
- `DELETE /api/users/{id}`: 특정 사용자를 삭제하는 엔드포인트.

이러한 엔드포인트는 클라이언트가 원하는 작업을 서버에 요청하고 응답을 받는 데 사용됩니다. API 디자인에서 엔드포인트를 명확하게 정의하고 문서화하는 것이 중요하며, 이를 통해 다른 개발자가 API를 쉽게 이해하고 사용할 수 있습니다.

---


