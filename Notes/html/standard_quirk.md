# 표준 모드 vs 호환 모드

### 과거 웹 페이지

- 넷스케이프 내비게이터용과 인터넷 익스플로러용의 두 가지 버전으로 만들어짐
- W3C의 웹 표준으로 인해 브라우저가 웹 사이트를 제대로 표현할 수 없게 되자 렌더링을 할 때 **표준 모드**와 **호환 모드**로 렌더링을 할 수 있게 옵션을 제공함.

---

### 표준 모드(Standards mode) VS 호환 모드(Quirks mode)

#### 표준 모드와 호환 모드는 [이 글](https://github.com/HyeongSeoku/Front_End_Must_know/blob/master/Notes/html/doctype.md)과 관련이 깊다.

<br>

브라우저는 HTML 문서가 **DOCTYPE**을 가지고 있지 않으면 호환 모드로 렌더링을 하고, 가지고 있다면 주어진 DOCTYPE에 맞게 표준 모드로 렌더링을 한다.

**호환 모드**로 렌더링을 하게 되면 오래된 웹페이지들을 최신 버전의 브라우저에서도 깨지지 않게 하기 때문에 각 브라우저마다 다르게 보일 수 있다.

#### 결론적으로 일반적인 경우 **DOCTYPE을 명시하여 브라우저가 _표준 모드_ 로 렌더링 하게 해야 한다**.

## 참고

- [MDN 표준모드와 호환 모드](https://developer.mozilla.org/ko/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)
- [[HTML] 표준 모드(Standards mode) VS 호환 모드(Quirks mode)
  ](https://sw-ryu.tistory.com/86)
