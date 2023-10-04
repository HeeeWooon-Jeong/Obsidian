**주요 특징 및 개념:**

1. **드라이버(Java Database Driver):** JDBC 드라이버는 특정 데이터베이스 관리 시스템과의 통신을 담당하는 소프트웨어 모듈입니다. 각 데이터베이스 벤더(Oracle, MySQL, PostgreSQL 등)는 자체 JDBC 드라이버를 제공합니다.

2. **JDBC URL:** JDBC URL은 데이터베이스에 연결할 때 사용하는 URL입니다. JDBC URL에는 데이터베이스 유형, 호스트 주소, 포트 번호, 데이터베이스 이름 등의 정보가 포함됩니다.

3. **Connection(연결):** `Connection`은 데이터베이스와의 연결을 나타내는 객체입니다. JDBC를 사용하여 데이터베이스에 연결하기 위해 `DriverManager`를 사용하고, `Connection` 객체를 얻을 수 있습니다.

4. **Statement(문장):** `Statement` 객체는 SQL 쿼리를 실행하기 위한 기본 수단입니다. `Statement`는 정적인 SQL 문장을 실행하며, `PreparedStatement`와 `CallableStatement`와 같은 특수한 서브클래스가 쿼리 파라미터화 및 저장 프로시저 호출과 같은 고급 작업을 지원합니다.

5. **ResultSet(결과 집합):** `ResultSet`은 SQL 쿼리의 결과 집합을 나타내는 객체입니다. `ResultSet`을 사용하여 쿼리 결과를 반복하고 검색할 수 있습니다.

6. **예외 처리:** JDBC 작업 중에 발생할 수 있는 예외(예: 데이터베이스 연결 실패, SQL 오류)를 처리해야 합니다. JDBC 메서드는 `SQLException`을 던질 수 있으므로 예외 처리가 필요합니다.

**JDBC 사용 방법:**

1. **드라이버 로딩:** JDBC 드라이버를 로드해야 합니다. 이것은 `Class.forName()` 메서드를 사용하여 수행할 수 있습니다. 예를 들어, MySQL 데이터베이스에 연결하려면 MySQL JDBC 드라이버를 로드해야 합니다.

2. **데이터베이스 연결:** `DriverManager.getConnection()` 메서드를 사용하여 데이터베이스에 연결합니다. 이 메서드는 JDBC URL, 사용자 이름 및 비밀번호를 인수로 사용합니다.

3. **SQL 쿼리 실행:** `Statement` 또는 `PreparedStatement` 객체를 사용하여 SQL 쿼리를 실행합니다. 쿼리 실행 결과는 `ResultSet` 객체에 저장됩니다.

4. **결과 처리:** `ResultSet`을 사용하여 쿼리 결과를 반복하고 데이터를 검색합니다.

5. **연결 해제:** JDBC 연결은 사용이 끝나면 반드시 닫아야 합니다. `Connection`, `Statement`, `ResultSet` 등의 자원을 명시적으로 해제합니다.

간단한 JDBC 코드 예시:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JDBCDemo {
    public static void main(String[] args) {
        String jdbcUrl = "jdbc:mysql://localhost:3306/mydatabase";
        String username = "myuser";
        String password = "mypassword";

        try {
            // 드라이버 로드
            Class.forName("com.mysql.cj.jdbc.Driver");

            // 데이터베이스에 연결
            Connection connection = DriverManager.getConnection(jdbcUrl, username, password);

            // SQL 쿼리 실행
            Statement statement = connection.createStatement();
            ResultSet resultSet = statement.executeQuery("SELECT * FROM employees");

            // 결과 처리
            while (resultSet.next()) {
                int id = resultSet.getInt("id");
                String name = resultSet.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }

            // 연결 해제
            resultSet.close();
            statement.close();
            connection.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

이 예제에서는 MySQL 데이터베이스와의 연결을 설정하고 몇 가지 간단한 데이터를 검색하는 기본적인 JDBC 코드를 보여줍니다. JDBC를 사용하면 Java 애플리케이션에서 데이터베이스와 손쉽게 상호 작용할 수 있습니다.
