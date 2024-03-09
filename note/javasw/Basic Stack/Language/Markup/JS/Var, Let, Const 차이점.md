### 날짜 : 2024-01-17 12:24

___

### 주제 : #Var #Let #Const

___

### Var : 

>[!note] 특징 = 변수
>
> 범위는 기본적으로 변수를 사용할 수 있는 위치를 의미합니다. 
> `var` 선언은 전역 범위 혹은 함수 범위로 지정됩니다.
> 
> `var`변수가 함수 외부에서 선언될 때의 범위는 전역입니다. 
> 즉, 함수 블록 외부에서 `var`를 사용하여 선언된 모든 변수를 전체 윈도우 상에서 사용할 수 있는 것이죠.
> 
> `var`가 함수 내에서 선언될 때는 함수 범위로 지정됩니다. 
> 즉, 해당 함수 내에서만 사용하고 접근할 수 있습니다.

>[!note] 호이스팅
> 
> 호이스팅이란 변수와 함수 선언이 맨 위로 이동되는 자바스크립트 매커니즘인데요. 
> 
> 예제) 코드
> 
> ```javascript
> console.log (greeter);
> var greeter = "say hello"
> ```
> 
> 예제) 코드 해석
> 
> ```javascript
> 1) var greeter;
> 2) console.log(greeter); // greeter is undefined
> 3) greeter = "say hello"
>```
>
>> `var`변수는 범위 내에서 맨 위로 올려지고, 값은 `undefined(정의되지 않음)`으로 초기화됩니다.

### Let

>[!note] 특징 = 변수
>
> `var` 선언에 대한 개선을 반영한 `let`이 현재 변수 선언에서 선호되고 있습니다. 

>[!note] 호이스팅
>
> `var`와 마찬가지로 `let` 선언은 맨 위로 끌어올려집니다. 
> `undefined(정의되지 않음)`으로 초기화되는 `var`와 다르게 `let`의 키워드는 초기화되지 않습니다. 
> 선언 이전에 `let` 변수를 사용하려고 시도한다면 `Reference Error(참조 오류)`가 발생할 것입니다.
> 
> 예제) 코드
> 
> ```javascript
> let greeting = "say Hi";
> greeting = "say Hello instead";
> ```
> 
> 예제) 코드 해석
> 
> ```javascript
> let greeting = "say Hi";
> let greeting = "say Hello instead"; 
> // error: Identifier 'greeting' has already been declared
> ```
>> 그러나 동일한 변수가 다른 범위 내에서 정의된다면, 에러는 더 이상 발생하지 않습니다.
> 
> 예제) 에러 해결 코드
> 
> ```javascript
> let greeting = "say Hi";
> if (true) {
> 	let greeting = "say Hello instead";
> 	console.log(greeting); // "say Hello instead"
> }
> console.log(greeting); // "say Hi"
> ```

>[!note] 호이스팅 에러 해결에 대한 이유
>
> 두 예제가 서로 다른 범위를 가지므로 서로 다른 변수로 취급되기 때문입니다. 
> 따라서 `var`보다 `let`이 더 나은 선택이 될 수 있는 것이죠. 
> `let`을 사용하는 경우라면, 변수가 범위 내에서만 존재하기 때문에 이전에 이미 사용한 적이 있는 변수 명에 대해서 더 이상 신경쓰지 않아도 좋습니다.
> 또한, 범위 내에서 동일한 변수를 두 번 이상 선언할 수 없기 때문에 앞서 설명한 `var`의 문제가 발생하지 않습니다.

### Const

>[!note] 특징 = 상수
>
> `const`로 선언된 변수는 일정한 상수 값을 유지합니다.
> `const` 선언은 `let` 선언과 몇 가지 유사점을 공유합니다.

>[!note] 호이스팅
>
> `let`과 마찬가지로 `const` 선언도 맨 위로 끌어올려지지만, 초기화되지는 않습니다.
> `const`로 선언된 변수의 값이 해당 범위 내에서 동일하게 유지됨을 의미합니다. 
> 업데이트하거나 다시 선언할 수가 없는 것입니다. 
> 
> 예제) 에러 
> ```javascript
> const greeting = "say Hi";
> greeting = "say Hello instead";
> // error: Assignment to constant variable. 
> ```
> 
> ```javascript
   > const greeting = "say Hi";
   > const greeting = "say Hello instead";
   > // error: Identifier 'greeting' has already been declared
> ```
> 
>> 따라서 모든 `const` 선언은 선언하는 당시에 초기화되어야 합니다. 

### Var, Let, Const 차이점

- `var` 선언은 전역 범위 또는 함수 범위이며, `let`과 `const`는 블록 범위이다.
- `var` 변수는 범위 내에서 업데이트 및 재선언할 수 있다. `let` 변수는 업데이트할 수 있지만, 재선언은 할 수 없다. `const` 변수는 업데이트와 재선언 둘 다 불가능하다.
- 세 가지 모두 최상위로 호이스팅된다. 하지만 `var` 변수만 `undefined(정의되지 않음)`으로 초기화되고 `let`과 `const` 변수는 초기화되지 않는다.
- `var`와 `let`은 초기화하지 않은 상태에서 선언할 수 있지만, `const`는 선언 중에 초기화해야한다.


___

### 출처(참고문헌)

- [Var, Let, Const의 차이점은?](https://www.freecodecamp.org/korean/news/var-let-constyi-caijeomeun/)

___

### 연결문서

- [[0.JS]]

