## ☑️`<!DOCTYPE Html>`

- ‘이 문서는 **HTML Living Standard 문서!**’라는 의미
  - html Living Standard란?
    - html의 살아있는 표준, 즉 html 최신 버전
    - html5를 최신 버전으로 알고 있는 경우가 많은데 이는 틀린 정보
- ❓해당 텍스트를 html 파일 최상단에 작성하지 않으면 어떻게 되나?
  - 그럼에도 문제없이 브라우저가 알아서 렌더링 해준다
    - 이유는? 사용자 경험을 향상시키기 위해서 우선 렌더링 시키기 위함이다. 최소한의 사용자 경험을 보존하기 위해서
    - 이 외에도 html 문법상 오류도 알려주지 않고 브라우저가 임의로 렌더링한다. 이 경우 개발자가 의도하지 않은 화면을 사용자에게 보여주게 될 우려가 있다.
- Quirks Mode
  - 오래된 웹 문서를 최신의 브라우저 환경에 맞게 렌더링하기 위한 모드
  - `<!DOCTYPE Html>` 이 html 문서 최상단에 존재하는 경우 Standard Mode로 렌더링되지만 그 외의 오래된 문서들은 Quirks Mode, Limited-Quirks Mode 등의 다른 모드를 통해 렌더링 된다.
  [Quirks Mode - HTML: HyperText Markup Language | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)

### 🔓 Screen Reader

[What is a screen reader? | Axess Lab](https://axesslab.com/what-is-a-screen-reader/)

## ☑️ HTML 기본 요소

### 1. 태그(Tag)

- 어떤 표시를 하기 위해 붙인 꼬리표. 웹 문서에 정보를 정의해주는 형식이다.
- 각각의 태그는 콘텐츠의 의미와 때때로 역할을 정의해주기도 한다.
- 기본적으로 `<>` 시작태그와 `</>` 종료태그의 쌍으로 구성되어 있다.
- ex. `<div></div>` `<p></p>`

### 2. 빈 요소 / 셀프 클로징(Self-closing) 태그

- 닫는 태그가 없는 태그
  ```html
  <br />
  <input type="text" />
  <img src="" alt="" />
  ```

### 3. 부모, 형제, 자식, 자손

- html 태그는 기본적으로 부모 / 자식의 관계로 이루어져 있다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/f84fcd11-81cc-4d31-945c-0b915c4a2ec2/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/fa3cad72-c854-4da1-9740-4b66a0781db2/Untitled.png)

## ☑️ Block/Inline/Inline-block

[HTML Block and Inline Elements](https://www.w3schools.com/html/html_blocks.asp)

### 1. Block

- 부모 요소의 전체 공간을 차지하여 블록을 만든다.
- 언제나 새로운 줄에서 시작, 좌우 양측으로 최대한 늘어나 가능한 모든 너비를 차지한다.
- 이전, 이후 요소 사이에 줄 바꿈이 일어난다.
- 페이지의 구조적 요소를 나타날 때 사용한다.
- 블록 요소로 대표적으로 사용되는 두 가지 태그에는 `<p>`, `<div>`가 있다.(Two commonly used block elements are: `<p>` and `<div>`. _ref: w3schools_)
- 블록요소는 인라인 요소 안에 중첩될 수 없지만, 인라인 요소는 블록 요소 안에 중첩될 수 있다.

```html
<!-- O -->
<**div**>
	블록요소 안
	<**span**>인라인요소 중첩 가능</**span**>
</**div**>

<!-- X -->
<**span**>
	인라인요소 안
	<**div**>블록요소 중첩 불가능</**div**>
</**span**>
```

❗️단, 인라인 요소 중 a 태그 안에서는 블록 요소 중첩이 가능하다.

```html
<!-- 가능 -->
<a href="#">
  <div></div>
</a>
```

### 2. Inline

- 항상 블록 레벨 요소 내에 포함된다.
- 콘텐츠의 흐름을 끊지 않으며, 콘텐츠에 따라 할당된 공간만 차지한다.
- 문장, 단어 같은 작은 부분으로 적용된다.
- 줄바꿈이 일어나지 않는다.
- width, height 크기를 지정할 수 없고, padding, border, margin 속성을 사용할 수 있지만, 상하 margin 속성은 사용할 수 없다.
- `<a>`, `<label>`, `<input>` 등이 있다.

### 3. block / inline / inline-block

|                                         | block                 | inline              | inline-block |
| --------------------------------------- | --------------------- | ------------------- | ------------ |
| 요소 포함                               | 인라인 요소 포함 가능 | 블록 요소 포함 불가 |
| (a 태그만 가능)                         | -                     |
| 줄바꿈                                  | O                     |
| (세로로 쌓임)                           | X                     |
| (가로로 쌓임)                           | X                     |
| (가로로 쌓임)                           |
| width, height                           | O                     | X                   | O            |
| padding                                 | O                     | O                   | O            |
| margin                                  | O                     | △                   |
| (left,right만 적용 / top,bottom 적용 X) | O                     |
| border                                  | O                     | O                   | O            |

## ☑️ 주요 태그

### 1. div

- 콘텐츠 분할 요소. 여러 태그들을 그룹핑하기 위한 태그이다.
- block-level element 이다.
- css로 스타일을 주기 전에는 콘텐츠나 레이아웃에 어떠한 영향도 주지 않는다(즉, 콘텐츠 자체에 의미를 주는 태그는 아님).
- 콘텐츠의 분할만을 위해 “**적절히**” 사용될 것을 권장함. 이 외에 header, footer, main, section, article, nav 등 다양한 시멘틱한 태그들을 활용하여 콘텐츠를 그룹핑 하는 것이 기본.

### 2. span

- 인라인 요소이다.
- div와 마찬가지로 css로 스타일을 주기 전에는 콘텐츠나 레이아웃에 어떠한 영향도 주지 않는다.

### 3. nav

- navigation bar
- 문서에서 현재 페이지 내 또는 다른 페이지로의 링크를 보여준다.

```html
<nav>
  <ul>
    <li><a href="#">메일</a></li>
    <li><a href="#">뉴스홈</a></li>
    <li><a href="#">쇼핑</a></li>
  </ul>
</nav>
```

- 메뉴, 목차, 브레드크럼(Breadcrumb)으로 사용된다.(Breadcrumb이란 말 그대로 직역하면 빵 부스러기란 뜻으로, 사용자의 페이지 이동 히스토리를 말한다. 한 마디로 사용자가 페이지 링크를 타고 타고 들어온 이력)

```html
<nav>
  <ol>
    <li><a href="#">쇼핑</a></li>
    <li><a href="#">의류</a></li>
    <li>여성의류</li>
  </ol>
</nav>
```

- 문서의 모든 링크가 `<nav>` 안에 있을 필요는 없다. 또한 하나의 웹페이지 내에 여러개의 `<nav>` 태그를 가질 수 있다.

### 4. a

- 다른 페이지나 같은 페이지의 어느 위치, 파일, 이메일 주소와 그 외 다른 URL로 연결할 수 있는 하이퍼링크를 만든다.
- `href` : hypertext reference
  - `tel` : 전화번호
  - `mailto` : 이메일 주소
- `target` 속성값
  - `_self` : 현재 페이지(기본값)
  - `_blank` : 새 탭
- `download`: 링크 이동 대신 사용자에게 URL에 위치한 대상을 다운로드 받을 지 물어본다. 이 때 브라우저에서 바로 열 수 있는 파일 포맷이라면 바로 실행한다.

```html
<a href="b.html">b.html으로 이동</a>
<a href="b.html" **target="_blank" **>b.html **새탭으로** 이동</a>
<a href="b.html" **download**>b.html 파일 **다운로드**</a>
<a href="**mailto**:google@gmail.com">mailto:google@gmail.com</a>
<a href="**tel**:010-0000-0000">010-0000-0000</a>
```

- `<a>` 태그는 인라인 요소이지만 예외적으로 블록 요소들을 감쌀 수 있다.
- `href` 속성과 `id` 를 사용하여 페이지 내에서 이동하는 해시 링크를 만들 수 있다.

### 5. p

- paragraph의 약어로 하나의 문단을 나타낸다.
- 블록 요소이다.

### 6. br

- break(line break)의 약어로 줄바꿈을 의미한다.
- self-closing 태그이다(닫는 태그가 필요없다).

### ❓Base64 format

- Base64 Encoding은 Binary Data를 Text로 변경하는 Encoding이다.
- Google 이미지 검색 시 이미지 리스트에 보이는 이미지들 중 경로가 Base64 인코딩이 되어있는 경우가 있다.

[Base64 - MDN Web Docs Glossary: Definitions of Web-related terms | MDN](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
