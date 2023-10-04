
> [!NOTE] JSTL
> JSTL(JSP Standard Tag Library)은 JavaServer Pages(JSP)에서 자주 사용되는 태그와 함수들의 라이브러리입니다. 
> 이 라이브러리는 JSP 페이지에서 자바 코드보다 더 간결하고 가독성이 높은 코드를 작성할 수 있게 도와줍니다. 
> 주로 웹 애플리케이션의 프레젠테이션 레이어에서 데이터를 표시하고 조작하는 데 사용됩니다.

1. **컨트롤 흐름 태그(Core Tags)**: JSTL의 핵심 기능 중 하나로, 조건문, 반복문 및 변수 설정을 처리하는 데 사용됩니다. 예를 들어 `<c:if>`, `<c:forEach>`, `<c:set>` 등이 있습니다.

2. **포맷팅 태그(Formatting Tags)**: 숫자, 날짜 및 시간과 같은 데이터를 형식화하고 출력하는 데 사용됩니다. `<fmt:formatNumber>`, `<fmt:formatDate>`, `<fmt:parseDate>` 등이 있습니다.

3. **데이터베이스 액세스 태그(SQL Tags)**: 데이터베이스에서 데이터를 조회하고 처리하는 데 사용됩니다. `<sql:setDataSource>`, `<sql:query>`, `<sql:update>` 등이 있습니다. 이러한 태그들을 사용하려면 서버에 JDBC 드라이버가 설정되어 있어야 합니다.

4. **XML 처리 태그(XML Tags)**: XML 데이터를 처리하고 조작하는 데 사용됩니다. `<x:parse>`, `<x:out>`, `<x:set>` 등이 있습니다.

5. **함수 태그(Functions Tags)**: 문자열 조작, 수학 연산, 날짜 계산과 같은 다양한 작업을 수행하는 데 사용됩니다. `<fn:substring>`, `<fn:length>`, `<fn:contains>` 등이 있습니다.

JSTL을 사용하면 JSP 페이지에서 자바 코드를 최소화하고 태그 기반의 템플릿 언어를 사용하여 웹 페이지를 작성할 수 있습니다. 이로써 코드의 가독성이 높아지고 유지 보수가 더 쉬워집니다.

JSTL 태그는 보통 JSP 페이지의 상단에서 다음과 같이 선언됩니다:

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/sql" prefix="sql" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>
```

그런 다음 선언한 태그 라이브러리의 접두사를 사용하여 JSTL 태그를 JSP 페이지에서 사용할 수 있습니다.
