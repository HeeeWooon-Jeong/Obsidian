(https://www.appletong.com/entry/Spring-PathVariable)

### Spring @PathVariable 어노테이션 쉽게 정리

REST API호출 경험이 있다면, URI값에 가변형 변수를 전달해서 처리하는 방식을 본적이 있을것이다.

```
http://127.0.0.1/users?userId={$userId}

http://127.0.0.1/users/{userId}
```

위에는 일반적인 GET 방식의 파라미터 전달이라 흔히 볼수있었다.

아래는 케이스는 Rest Api호출시 주로 많이 사용하게 된다.

URI를 이용해 파라미터 처리를 할수있다는 뜻이다.