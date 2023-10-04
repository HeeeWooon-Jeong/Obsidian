



> [!NOTE] # 스프링 빈(Spring Bean)이란?
> 
> `Spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)`이라고 부릅니다. 
> IOC의 특징은 아래와 같습니다.

> - 일반적으로 처음에 배우는 자바 프로그램에서는 **각 객체들이 프로그램의 흐름을 결정하고 각 객체를 직접 생성하고 조작하는 작업(객체를 직접 생성하여 메소드 호출)을 했습니다**.
>    즉, 모든 작업을 사용자가 제어하는 구조였습니다. 예를 들어 A 객체에서 B 객체에 있는
>    메소드를 사용하고 싶으면, B 객체를 직접 A 객체 내에서 생성하고 메소드를 호출합니다.
> - 하지만 **IOC가 적용된 경우, 객체의 생성을 특별한 관리 위임 주체에게 맡깁니다.** 
>    이 경우 **사용자는 객체를 직접 생성하지 않고, 객체의 생명주기를 컨트롤하는 주체는 다른 주체**가 됩니다. 
>    즉, 사용자의 제어권을 다른 주체에게 넘기는 것을 IOC(제어의 역전) 라고 합니다.

우리가 알던 기존의 Java Programming 에서는 Class를 생성하고 new를 입력하여 원하는 객체를 직접 생성한 후에 사용했었습니다. 
하지만 Spring에서는 직접 new를 이용하여 생성한 객체가 아니라, Spring에 의하여 관리당하는 
자바 객체를 사용합니다. 
이렇게 **Spring에 의하여 생성되고 관리되는 자바 객체를 Bean**이라고 합니다. 
Spring Framework 에서는 Spring Bean 을 얻기 위하여 ApplicationContext.getBean() 와 같은 메소드를 사용하여 Spring 에서 직접 자바 객체를 얻어서 사용합니다.

Spring에서는 여러 가지 Annotation을 사용하지만, Bean을 등록하기 위해서는 @Component Annotation을 사용합니다. 

**@Component Annotation이 등록되어 있는 경우에는 Spring이 Annotation을 확인하고 자체적으로 Bean 으로 등록**합니다.

실제로 사용되는 예시를 볼까요? 실제 Spring 프로젝트에서 Controller를 등록할 때에는 아래와 같은 **Annotation**을 사용합니다. 아래의 예시에서 Controller 임을 Spring 에게 알려주기 위하여 **@Controller Annotation**을 사용했습니다.

```java
// HelloController.java
@Controller
public class HelloController {
    // Http Get method 의 /hello 경로로 요청이 들어올 때 처리할 Method를 아래와 같이 @GetMapping Annotation을 사용하여 Mapping을 사용할 수 있습니다.
    @GetMapping("hello")
    public String hello(Model model){
        model.addAttribute("data", "This is data!!");
        return "hello";
    }
}
```

@Controller Annotation을 intelliJ에서 Ctrl 을 눌러서 이동해보면 아래와 같은 소스를 확인할 수 있습니다. @Controller Annotation에는 @Component Annotation이 있는 것을 확인할 수 있습니다. @Component Annotation 으로 인하여 Spring은 해당 Controller를 Bean 으로 등록합니다.

```java
// Controller.java

// -- 일부 생략 --
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Controller {

	/**
	 * The value may indicate a suggestion for a logical component name,
	 * to be turned into a Spring bean in case of an autodetected component.
	 * @return the suggested component name, if any (or empty String otherwise)
	 */
	@AliasFor(annotation = Component.class)
	String value() default "";

}
```

### 2.2. Bean Configuration File에 직접 Bean 등록하는 방법

@Configuration과 @Bean Annotation 을 이용하여 Bean을 등록할 수 있습니다. 아래의 예제와 같이 @Configuration을 이용하면 Spring Project 에서의 Configuration 역할을 하는 Class를 지정할 수 있습니다. 해당 File 하위에 Bean 으로 등록하고자 하는 Class에 @Bean Annotation을 사용해주면 간단하게 Bean을 등록할 수 있습니다.

```java
// Hello.java
@Configuration
public class HelloConfiguration {
    @Bean
    public HelloController sampleController() {
        return new SampleController;
    }
}
```
<br>
<br><br>
<br><br>






## GPT

> [!NOTE] Bean
> "빈(Bean)"은 소프트웨어 개발에서 사용되는 중요한 개념 중 하나입니다. 주로 Java와 관련된 기술 스택에서 많이 사용되며, Spring Framework와 같은 프레임워크에서도 중요한 역할을 합니다.
빈의 개념은 다음과 같이 설명할 수 있습니다:

1. **객체(Objects)**: 빈은 일반적으로 객체를 나타냅니다. 즉, 클래스의 인스턴스입니다. 이 객체는 어플리케이션에서 사용하는 데이터나 기능을 캡슐화하고 있습니다.

2. **재사용성**: 빈은 코드 내에서 여러 곳에서 재사용할 수 있는 독립적인 모듈입니다. 이는 코드의 재사용성과 유지 보수성을 향상시키는 데 도움이 됩니다.

3. **의존성 주입**: 많은 프레임워크와 컨테이너는 빈을 관리하고 의존성을 주입하는 데 사용됩니다. 예를 들어, Spring Framework에서는 빈을 Spring 컨테이너에 등록하고 필요한 다른 빈에 주입할 수 있습니다.

4. **라이프사이클 관리**: 빈은 생명주기(lifecycle)를 가지며, 생성부터 소멸까지의 여러 이벤트를 관리할 수 있습니다. 이를 통해 초기화, 종료 및 리소스 관리 등을 수행할 수 있습니다.

5. **설정 파일 또는 어노테이션**: 빈은 일반적으로 XML 설정 파일이나 어노테이션을 통해 정의됩니다. Spring과 같은 프레임워크는 이러한 설정 정보를 기반으로 빈을 생성하고 관리합니다.

6. **스코프**: 빈은 다양한 스코프(예: 싱글톤, 프로토타입)를 가질 수 있으며, 스코프에 따라 빈의 인스턴스가 관리됩니다.

예를 들어, Spring Framework에서는 Java 클래스를 빈으로 정의하고 Spring 컨테이너에 등록하여 관리합니다. 이를 통해 객체 간의 의존성 주입, 라이프사이클 관리, 트랜잭션 관리 등을 쉽게 구현할 수 있습니다.

빈의 개념은 객체 지향 프로그래밍과 의존성 주입(Dependency Injection) 패턴과 밀접하게 관련되어 있으며, 모듈화와 코드의 재사용성을 높이는 데 도움을 줍니다.
## [빈 설명](https://melonicedlatte.com/2021/07/11/232800.html)


