
> [!NOTE] # @ModelAttribute
> 
> 
> 컨트롤러 메서드에 사용되며 해당 메서드의 리턴 값을 모델에 추가하는 데 사용됩니다. 
> 주로 웹 애플리케이션에서 사용자에게 데이터를 보여주기 위해 뷰로 데이터를 전달할 때 
> 사용됩니다.

`@ModelAttribute`는 사용자가 요청시 전달하는 값을 오브젝트 형태로 매핑해주는 어노테이션입니다.

`@ModelAttribute`를 사용하는 방법과 주요 특징은 다음과 같습니다:

1. **메서드 레벨에서 사용**: `@ModelAttribute` 애노테이션은 컨트롤러 클래스의 메서드 레벨에서 사용됩니다. 이 메서드는 해당 컨트롤러에서 처리되는 모든 요청에 대해 호출됩니다.

   ```java
   @Controller
   public class MyController {
       @ModelAttribute("myData")
       public MyDataModel populateDataModel() {
           // 모델 데이터를 초기화하거나 가져옴
           return new MyDataModel();
       }

       // 다른 컨트롤러 메서드들...
   }
   ```

2. **메서드의 리턴 값을 모델에 추가**: `@ModelAttribute`가 적용된 메서드의 리턴 값은 모델에 추가됩니다. 이 모델 객체는 뷰에서 데이터를 표시하는 데 사용됩니다.

3. **모델 속성 이름 지정**: `@ModelAttribute` 애노테이션은 속성의 이름을 지정할 수 있습니다. `@ModelAttribute("myData")`와 같이 사용하면 모델에 추가되는 속성의 이름을 "myData"로 지정합니다. 뷰에서는 이 이름을 사용하여 해당 데이터에 접근할 수 있습니다.

5. **자동으로 바인딩**: `@ModelAttribute`를 사용하면 요청 파라미터와 모델 객체 사이의 데이터 바인딩을 자동으로 처리합니다. 요청 파라미터와 모델 객체의 필드 이름이 일치하면 자동으로 값을 할당합니다.

   ```java
   @PostMapping("/saveData")
   public String saveData(@ModelAttribute("myData") MyDataModel myData) {
       // myData 객체에는 요청 파라미터가 자동으로 바인딩됨
       // 이후 로직...
       return "resultPage";
   }
   ```

5. **뷰에서 사용**: 모델에 추가된 데이터는 뷰 템플릿에서 `${myData}`와 같이 EL(표현 언어)을 사용하여 접근할 수 있습니다.

`@ModelAttribute`를 사용하면 컨트롤러 메서드에서 초기화하거나 가져온 데이터를 뷰로 전달하기가 편리해집니다. 
이를 통해 웹 애플리케이션의 데이터 흐름을 관리하고 사용자에게 데이터를 효과적으로 표시하는 데 도움이 됩니다.

---

[블로그](https://blog.karsei.pe.kr/59)
@ModelAttribute 는 **parameter**, **method** 레벨로 두 가지의 방식을 지원하고 있다.

---

[쉬운버전?](https://dev-coco.tistory.com/100)

---

[블로그2](https://galid1.tistory.com/769)
@RequestParam도 같이