
> [!NOTE] PageContext
> `pageContext`는 JSP 페이지에서 사용할 수 있는 내장 객체(Built-in Object) 중 하나입니다. 
> 이 객체는 JSP 페이지와 관련된 다양한 정보와 기능을 제공합니다. 
> `pageContext` 객체는 다음과 같은 주요 기능을 수행할 수 있습니다:

1. **Request 정보 접근**: `pageContext`를 사용하여 HTTP 요청(Request) 관련 정보에 접근할 수 있습니다. 예를 들어, `pageContext.getRequest()`를 호출하여 현재 요청 객체에 접근할 수 있습니다.

2. **Session 관리**: `pageContext`를 사용하여 세션(Session) 객체를 가져오거나 세션 속성을 설정할 수 있습니다. `pageContext.getSession()`을 호출하여 현재 세션에 접근할 수 있습니다.

3. **Application 정보 접근**: `pageContext`를 사용하여 웹 애플리케이션의 전역 정보에 접근할 수 있습니다. `pageContext.getServletContext()`를 호출하여 서블릿 컨텍스트에 접근할 수 있습니다.

4. **Page Scope 변수**: `pageContext`를 사용하여 페이지 스코프(Page Scope) 변수를 설정하고 검색할 수 있습니다. 페이지 스코프 변수는 현재 JSP 페이지 내에서만 사용 가능한 변수입니다.

5. **Forward 및 Include**: `pageContext`를 사용하여 다른 JSP 페이지로의 포워딩(Forward) 및 인클루드(Include) 작업을 수행할 수 있습니다.

6. **EL(Expression Language) 평가**: EL 표현식을 사용하여 JSP 페이지에서 변수를 평가하고 결과를 가져올 때 `pageContext`를 사용합니다. 예를 들어 `${pageContext.request}`와 같이 EL을 사용할 수 있습니다.

7. **내장 객체 검색**: `pageContext`를 사용하여 다른 내장 객체인 `request`, `response`, `session`, `application` 등에 접근할 수 있습니다.

`pageContext` 객체는 JSP 페이지 내에서 자동으로 사용 가능하며, 주로 웹 애플리케이션의 상태 및 정보에 접근하거나 JSP 페이지 간에 데이터를 공유할 때 유용하게 사용됩니다.
