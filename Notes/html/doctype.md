# DOCTYPE

### 내가 작성하려는 HTML 문서가 어떤 문서 형식을 갖고 있는지 선언.

#### 문서 형식 선언이 없으면 **쿼크모드로** 렌더링을 해서 각 브라우저마다 다른 형태의 결과물을 보여주게 되는데 이것을 방지하기 위해 문서 형식 선언을 하고 그로인해 HTML 문서를 표준모드로 렌더링 할 수 있게된다

<br>

### 쿼크모드

    오래된 웹 페이지의 하위 호환성 유지를 위해 사용되며, W3C나 IETF의 표준을 엄격하게 준수하지  않는다. 같은 코드라도 웹 브라우저마다 다르게 해석해서 다른 결과물을 보여준다.

_[쿼크 모드](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)에 대한 더 자세한 정보_

---

## 선언 미선언 차이

`<!DOCTYPE>` **미 선언시** ➡️ 쿼크 모드로 랜더링 ➡️ **브라우저마다 다른 결과물 출력**
<br>

`<!DOCTYPE>` **선언시** ➡️ 표준 모드로 랜더링 ➡️ **브라우저마다 다른 결과물 출력**
<br>

---

### HTML5

#### HTML5의 경우 문서 형식 선언(DOCTYPE)이 불필요하지만 웹 브라우저들의 표준모드 활성화를 위해 최소한의 형태로 유지되어 사용된다

## 참고

- [MDN 문서 타입 정의](https://developer.mozilla.org/ko/docs/Glossary/Doctype)
- [HTML <!DOCTYPE> 선언](http://www.tcpschool.com/html-tags/doctype)
