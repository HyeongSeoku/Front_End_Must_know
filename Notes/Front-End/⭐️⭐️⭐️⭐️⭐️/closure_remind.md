# 클로저 (복습)

### 1.클로저란?

### 2.클로저의 원리와 왜 사용하는지에 대해 설명해 주세요.

<br>

# Anwer

## 스코프 (💡사전 지식)

- 식별자 접근 규칙에 따른 유효 범위
- 범위는 **중괄호(블록)** 또는 **함수**에 의해 나눠진다.
- 그 범위를 스코프라 함
- 각각 **Block Scope** 와 **Function Scope**라 함

_화살표 함수는 Block Scope 취급_

<br>

### 스코프의 규칙

**👉 규칙1. 안쪽 스코프에서 바깥쪽 스코프로 접근할 수 있지만 반대는 불가능하다.**

- 바깥쪽 스코프에서 선언한 식별자는 안쪽 스코프에서 사용 가능하다.
- 반면, 안쪽에서 선언한 식별자는 바깥쪽 스코프에서는 사용할 수 없다.

**👉 규칙2. 스코프는 중첩이 가능하다.**

- 스코프는 마치 중첩된 울타리와도 같다.

**👉 규칙3. 전역 스코프와 지역 스코프**

- 가장 바깥쪽의 스코프를 전역 스코프(Global Scope)라고 부른다.
- 전역이 아닌 다른 스코프는 전부 지역 스코프(Local Scope)이다.

**👉 규칙4. 지역 변수는 전역 변수보다 우선순위가 더 높다.**

- 전역 스코프에서 선언한 변수는 전역 변수이다.
- 지역 스코프에서 선언한 변수는 지역 변수이다.
- 지역 변수는 전역 변수보다 더 높은 우선순위를 가진다.

<br>

## 클로저란

- ### 어떤 함수 A에서 선언한 변수 a를 참조하는 내부함수 B를 외부로 전달할 경우, A의 실행 컨텍스트가 끝난 뒤에도 변수 a가 사라지지 않는 현상 - 코어 자바스크립트(정재남)
- ### 함수와 자신이 선언됐을때의 렉시컬 환경(Lexical environment)과의 조합.

> 여러 함수형 프로그래밍 언어에서 등장하는 보편적인 특성

_클로저 : 현상_

_함수: 이 현상(클로저)가 나타나기 위한 조건_

---

<br>

## 클로저의 원리 & 사용 이유

### 클로저 예시

```js
let func1 = function () {
  let a = 1;

  let func2 = function () {
    return ++a;
  };
  return func2; //func2 함수 자체를 반환
};

let func3 = func1();
console.log(func3()); // 값: 2
console.log(func3()); // 값: 3
```

1. 변수 func3은 func2함수를 참조하게 됨
2. `console.log(func3())` 실행시 func2함수 실행되고 ++a를 한 값을 리턴하게 됨 (2)
3. 그 아래 줄의 `console.log(func3())` 실행시 역시 func2함수 실행되고 ++a를 한 값을 리턴하게 됨 (3)

> _참조 : 객체의 실제 위치를 가르키는 포인터_

### 클로저가 가능한 이유

> 가비지 컬렉터의 동작 방식 : 어떤 값을 참조하는 변수가 하나라도 있다면 그 값은 수집 대상에 포함하지 않는다.

---

<br>

### 사용 이유

1. 전역변수를 줄일 수 있다.

   ```js
   const btn = document.querySelector("button");

   btn.addEventListener("click", handleClick());

   function handleCilck() {
     let count = 0;
     return function () {
       count++;
       return count;
     };
   }
   ```

2. 비슷한 형태의 코드를 재사용률을 높일 수 있다. (모듈화에도 유리)

   ```js
   const newTag = function (open, close) {
     return function (content) {
       return open + content + close;
     };
   };

   const bold = newTag("<b>", "</b>");
   const italic = newTag("<i>", "</i>");

   console.log(bold(italic("This is my content!")));
   //<b><i>This is my content!</i></b>
   ```

3. 정보의 접근 제한 (캡슐화)를 시킬 수 있다.
4. 데이터를 보존할 수 있다.

### 클로저의 단점

- 메모리 누수 발생 가능
  - 사용후 메모리를 해제해 누수를 줄여야한다 (`closure1 = null`)
- 스코프 체인을 거슬러 올라가기 때문에, 조금 느림

## 클로저 사용 예시

- ### setTimeout을 사용한 예제 [오답]

```js
function count() {
  var i;
  for (i = 0; i < 5; i++) {
    setTimeout(function timer() {
      console.log(i);
    }, i * 1000);
  }
}
count();
```

> 작성자의 의도 💭 : 0,1,2,3,4가 1초 간격으로 출력되겠군 !
>
> 실제 출력결과 : 5,5,5,5,5

### 위 예제 해설

1. 첫 반복문의 상황 : i = 0, setTimeout함수와 함께 timer()함수가 작동하여 0\*1000ms 뒤의 i 값을 콘솔에 출력하도록 명령
2. 두번째 반복문 : i = 1 , setTimeout함수와 함께 timer()함수가 작동하여 1\*1000ms 뒤의 i 값을 콘솔에 출력하도록 명령
3. 세번째 반복문 : i = 2 , setTimeout함수와 함께 timer()함수가 작동하여 2\*1000ms 뒤의 i 값을 콘솔에 출력하도록 명령
4. i값 만 바뀔뿐 동작은 동일
5. 마찬가지로 i 값만 바뀜

<img width="400" src="https://user-images.githubusercontent.com/48541850/162130408-17b00e3a-dad7-4ef9-82b7-ace4e8f230d3.jpeg"/>

그림처럼 for문을 다 돌고나서의 timer()함수가 실행되는데. 클로저는 현재의 i즉 i=6인 상태를 참조하기 때문에
의도처럼 동작하지 않음

---

<br>

- ### setTimeout을 사용한 예제 [정답]
  > IIFE(즉시 사용 함수) + parameter

```js
function count() {
  var i;
  for (i = 0; i < 5; i++) {
    (function (countingNumber) {
      setTimeout(function () {
        console.log(countingNumber);
      }, i * 1000);
    })(i);
  }
}
count(); //0,1,2,3,4
```

> ES6에서 추가된 Block Scope (let을 이용)

```js
function count() {
  "use strict";
  for (let i = 0; i < 5; i++) {
    setTimeout(function timer() {
      console.log(i);
    }, i * 1000);
  }
}
count(); //0,1,2,3,4
//반복문이 실행될 때마다 클로저가 생성되므로 i는 각 시점의 i에 접근하여 증가하는 숫자를 출력할 수 있다.
```

## 참고

- [MDN 클로저](https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures)

- [[JavaScript] 스코프(Scope)와 변수 선언 (var, let, const 키워드 차이점)](https://hanamon.kr/javascript-%ec%8a%a4%ec%bd%94%ed%94%84%ec%99%80-%eb%b3%80%ec%88%98%ec%84%a0%ec%96%b8%ed%82%a4%ec%9b%8c%eb%93%9c-%ec%b0%a8%ec%9d%b4%ec%a0%90/)
- [⭐️ [JavaScript] 클로저(Closures)란 무엇일까?](https://hanamon.kr/javascript-%ED%81%B4%EB%A1%9C%EC%A0%80/)

- [[JS]클로져(closure)와 클로져의 사용 예제](https://velog.io/@proshy/JS%ED%81%B4%EB%A1%9C%EC%A0%B8closure%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%B8%EC%9D%98-%EC%82%AC%EC%9A%A9-%EC%98%88%EC%A0%9C)

- [Javascript - 나를 위한 클로저 예제 분석](https://pewww.tistory.com/21)
