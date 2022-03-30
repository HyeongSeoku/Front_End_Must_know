# 호이스팅

### 호이스팅에 대해서 설명해보세요.

<br>

## Anwer

---

### Hoisting

- 사전적 의미 : 끌어 올리다.
- **변수 또는 함수가 아래에 선언이 되어 있어도 최상단으로 끌어 올려진 것처럼 작동하는 것을 호이스팅이라한다.**

<br>

#### Hoisting의 이유

변수 선언이 소스코드가 한 줄씩 순차적으로 실행되는 시점, 즉 런타임이 아니라 그 이전 단계에서 먼저 실행되기 때문

<br>

### Hoisting의 종류

- 변수 호이스팅
- 함수 호이스팅

### 변수 호이스팅

var 키워드를 사용하여 변수 선언시 호이스팅됨

_let,const는 호이스팅 되지 않음._

<br>

---

var

```ts
var value;
console.log(value); //값 : undefined
```

let,const

```ts
let value2;
const value3;

console.log(value2); // error 발생
console.log(value3); // error 발생
```

### 함수 호이스팅

function 키워드 사용

```ts
first(); //first test function 출력

function first() {
  console.log("first test function");
}

//💡함수 선언문으로 함수 생성시 런타임 이전에 함수안에 있는 함수 객체들을 할당까지 완료.
```

### _호이스팅을 방지하는 법_

변수에 함수를 할당

```ts
log();
//에러 발생  Uncaught ReferenceError : Cannot access 'Log' before initialization

//ES6의 arrow function
const log = () => {
  console.log("Log");
};
```

### ❗️주의

var 키워드로 함수 할당시 다른 오류가 남.

```ts
log(); //변수 호이스팅 발생
//Error발생 : Uncaught TypeError : Log is not a function

var log = () => {
  console.log("Log");
};
```

---

### 유의할 점

#### ❗️ 실제로 코드가 끌어 올려지는 것은 아니며, 내부적으로 _끌어 올려진것 처럼_ 동작하는 것

<br>

## 정리

- **호이스팅** : 모든 선언문을 소스코드에서 찾아서 최상단으로 끌어 올려진 것처럼 실행하는 자바스크립트의 특징
- **변수 호이스팅과 함수 호이스팅이 있음**
  - 변수의 경우 _var_ 키워드로 선언된 변수만 호이스팅 되고 _let_,*const*로 선언시 호이스팅 되지 않음.
  - _var_ 키워드로 변수 선언 후 값 할당해주지 않으면 *undefined*로 초기화됨
  - 함수의 경우 함수 선언문으로 함수 생성시 호이스팅 되며 함수안에 있는 함수 객체들을 할당까지 완료됨.
- **함수 호이스팅을 막는법**
  - let,const를 이용하여 변수에 함수를 할당.
  - _❗️주의 할 점_ var 키워드 사용하여 변수에 함수 할당시 다른 에러 발생.

<br>

---

참고

[02.호이스팅](https://velog.io/@yhj96/02.-JS-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85Hoisting)

[[JavaScript] 호이스팅 (Hoisting)](https://gmlwjd9405.github.io/2019/04/22/javascript-hoisting.html)

📚 모던 자바스크립트 Deep Dive
