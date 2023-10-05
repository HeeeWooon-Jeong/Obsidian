

### **URI (Uniform Resource Identifier):**

- URI는 자원을 식별하고 이름을 지정하는 일반적인 개념입니다. URI는 리소스의 고유한 식별자이며, 리소스의 위치나 특성을 나타낼 수 있습니다.
- URI는 두 가지 하위 유형으로 나눌 수 있습니다: URL과 URN.
- 예: `mailto:example@example.com` (이메일 주소), `urn:isbn:0451450523` (도서 ISBN).

---
### **URL (Uniform Resource Locator):**

- URL은 URI의 하위 집합이며, 리소스의 위치를 지정하는 데 사용됩니다. 즉, URL은 리소스가 어디에 있는지를 나타냅니다.
- URL은 프로토콜(예: http, https), 호스트(예: [www.example.com](http://www.example.com/)), 포트(예: 80), 경로(예: /path/to/resource), 쿼리 문자열(예: ?key=value) 등으로 구성됩니다.
- 예: `http://www.example.com/index.html`, `https://api.example.com/data?format=json`.

---
### URN(Uniform Resource Name)

은 URI(Uniform Resource Identifier)의 하위 범주 중 하나입니다. URN은 리소스를 고유하게 식별하기 위한 목적으로 사용됩니다. URL과는 달리 리소스의 위치나 접근 방법을 나타내지 않고, 리소스의 이름을 나타냅니다.

URN의 주요 특징은 다음과 같습니다:

1. **고유성:** URN은 리소스의 고유한 이름 또는 식별자를 제공합니다. 이것은 리소스가 이동하더라도 그 이름이 변하지 않는다는 것을 의미합니다.

2. **영속성:** URN은 리소스가 지속적으로 존재하는 것을 나타냅니다. 따라서 리소스가 영구적으로 유지될 것으로 기대됩니다.

3. **인프라 독립성:** URN은 리소스의 위치나 분산 환경과 관련이 없으며, 특정 인프라스트럭처에 의존하지 않습니다.

4. **URN 형식:** URN은 일반적으로 다음과 같은 형식을 따릅니다: `urn:{namespace}:{resource-ID}`. 예를 들어, ISBN(국제 표준 도서 번호) URN의 형식은 다음과 같습니다: `urn:isbn:0451450523`.

URN은 주로 도서, 학술 논문, 문화적 자산 및 기타 영구적인 리소스를 식별하기 위해 사용됩니다. 
예를 들어, 도서의 ISBN은 URN으로 사용됩니다. 
URN은 리소스의 이름을 지정하고 검색하기 위한 목적으로 사용되며, 해당 리소스를 식별하기 위해 사용자가 이해하기 쉬운 형태의 이름을 제공합니다.

하지만 URL이 웹에서 리소스에 접근하는 데 사용되는 반면, URN은 리소스를 식별하고 이름을 지정하는 데 사용됩니다.

