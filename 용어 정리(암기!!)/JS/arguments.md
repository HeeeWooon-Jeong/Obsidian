
> [!NOTE] # arguments
> `arguments`는 JavaScript 함수 내에서 사용할 수 있는 특별한 객체입니다. 
> 이 객체는 현재 함수가 호출될 때 전달된 모든 인수(argument)를 저장하고 있는 배열처럼 동작합니다.

주로 다음과 같은 상황에서 `arguments` 객체를 사용합니다:

1. **가변 인자 함수 (Variadic Function):** 함수가 정해진 수의 매개변수를 가지지 않고, 다양한 수의 인수를 처리해야 할 때 사용됩니다. `arguments` 객체를 사용하여 인수를 동적으로 처리할 수 있습니다.

```javascript
function sum() {
  var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  return total;
}

console.log(sum(1, 2, 3)); // 6
console.log(sum(10, 20, 30, 40)); // 100
```

2. **함수 오버로딩 (Function Overloading):** JavaScript는 함수 오버로딩을 지원하지 않지만, `arguments`를 사용하여 다른 인수 조합에 대응하는 함수를 작성할 수 있습니다.

3. **매개변수의 수를 모를 때:** 함수가 얼마나 많은 인수를 받을지 미리 알 수 없는 경우에 `arguments`를 사용하여 인수를 처리합니다.

```javascript
function logArguments() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}

logArguments("Hello", 42, true);
```

`arguments` 객체는 배열과 비슷하지만 배열 메서드(예: `push`, `pop`, `forEach` 등)를 직접 사용할 수는 없습니다. 그러나 ES6부터는 나머지 매개변수(rest parameters)를 사용하여 가변 인자 함수를 더 간결하게 작성할 수 있습니다.
