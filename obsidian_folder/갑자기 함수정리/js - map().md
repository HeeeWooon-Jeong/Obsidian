`map()` 함수는 JavaScript에서 배열을 다룰 때 자주 사용되는 배열 메서드 중 하나입니다. 이 함수는 주어진 배열의 모든 요소에 대해 지정된 함수를 호출하고, 각 요소에 대한 새로운 배열을 생성합니다. 기본적으로 `map()`은 원래 배열을 변경하지 않고 새로운 배열을 반환합니다. 

`map()` 함수는 다음과 같은 구문을 가집니다:

```javascript
const newArray = array.map(callback(currentValue[, index[, array]])[, thisArg])
```

여기에서 각 매개변수의 역할은 다음과 같습니다:

- `array`: 원본 배열입니다.
- `callback`: 각 요소에 대해 호출되는 함수로, 다음과 같은 인수를 받습니다.
  - `currentValue`: 현재 처리 중인 배열 요소의 값입니다.
  - `index` (선택 사항): 현재 배열 요소의 인덱스입니다.
  - `array` (선택 사항): `map()`을 호출한 배열 자체입니다.
- `thisArg` (선택 사항): `callback` 함수 내에서 `this`로 참조될 객체입니다.

`map()` 함수는 다음과 같은 일반적인 용도로 사용됩니다:

1. **배열 변환:** 원본 배열의 각 요소를 새로운 값으로 변환하여 새로운 배열을 생성합니다. 이때 변환 작업은 `callback` 함수 내에서 수행됩니다.

2. **요소 수정:** 원본 배열의 각 요소를 수정하거나 가공하여 새로운 배열을 만듭니다.

3. **요소 필터링:** 조건에 맞는 요소만 선택하여 새로운 배열을 생성합니다.

예를 들어, 다음은 `map()` 함수를 사용하여 배열의 각 요소를 제곱하여 새로운 배열을 생성하는 간단한 예제입니다:

```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map((num) => num * num);
console.log(squaredNumbers); // [1, 4, 9, 16, 25]
```

이 예제에서 `map()` 함수는 `numbers` 배열의 각 요소를 제곱하여 `squaredNumbers` 배열을 생성합니다. `callback` 함수가 각 요소에 대한 변환 작업을 수행합니다.