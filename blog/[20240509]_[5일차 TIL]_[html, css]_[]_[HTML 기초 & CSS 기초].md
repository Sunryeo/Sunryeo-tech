# ☑️ 표(table)

- 테이블(표)를 생성할 때 사용한다.
- `table` 은 테이블 데이터의 컨테이너 요소이다.

## ✔️ tr / th / td

- `tr`: table row. 테이블의 행
- `th`: table header. 테이블의 행, 열의 제목을 나타내는 셀
- `td`: table data. 셀 내용
- `th` 또는 `td`는 `tr`로 감싸져야 한다.

## ✔️ caption

- 테이블의 제목이나 설명
- table의 첫번째 자식으로만 사용될 수 있음
- 선택적 요소
- CSS의 `caption-side` 속성(top, bottom)으로 위치를 설정할 수 있다.

```html
<table>
  <caption>
    설명
  </caption>
  <tr>
    <th>제목</th>
    <td>내용</td>
  </tr>
</table>
```

## ✔️ thead / tbody / tfoot

- 테이블의 머리글, 본문, 바닥글을 의미
- 구역을 나누는 용도로 사용됨, 선택적 요소
- `thead` → `tbody` → `tfoot` 순서대로 사용

## ✔️ colspan / rowspan

- 셀병합 속성
- `colspan`: 열 병합, `rowspan` : 행 병합
- 값은 숫자로 줄 수 있으며 숫자만큼 행 또는 열의 개수가 병합됨

```html
<tr>
  <td colspan="2" rowspan="2">&nbsp;</td>
  <th colspan="3">Clothes</th>
  <th colspan="2">Accessories</th>
</tr>
<tr>
  <th rowspan="3">Belgium</th>
</tr>
```

## ✔️ colgroup

- 테이블 열 그룹을 만들고 싶을 때 사용한다.
- `col`
  - 테이블 열을 하나 이상 묶을 때 사용한다. `colgroup` 내부에 포함되는 요소이다.
  - `span`: 선택할 영역 지정 속성, 숫자로 지정하여 몇개의 열을 한번에 선택할 지 결정

```html
<table>
  <colgroup>
    <col />
    <col span="2" class="batman" />
    <col span="2" class="flash" />
  </colgroup>
</table>
```

# ☑️ CSS

- CSS는 Cascading Style Sheets의 약자이다.(Cascading → 위에서 아래로 폭포처럼 떨어짐)
- HTML의 스타일, 레이아웃 등을 꾸미는 역할을 한다.

## ✔️ 기본 문법 및 요소

- 선택자(Selector) → html 태그, style을 주고자 하는 영역의 태그를 선택함
- 속성(Property)
- 속성값(Property Value)

```css
div {
  /* 선택자: div, {: 해당 태그의 스타일 적용 시작 */
  background-color: red; /* background-color: 속성, red: 속성값, ;으로 해당 속성 명령 종료 */
  border-radius: 4px;
} /* }: 스타일 적용 종료 */
```

## ✔️ CSS 적용 방식

### 1. 인라인 방식

- 태그 내부에 `style` 속성으로 스타일을 주는 방식
- `:hover` , `::before` , `::after` 같은 가상요소에는 사용불가

```html
<p **style="color:yellow; background-color:black;" **>Hello wold</p>
```

### 2. 내부 스타일

- `head` 태그 안 `style` 태그를 사용하여 스타일을 주는 방식
- `style` 코드가 길어질수록 html 파일의 크기가 커지기 때문에 비효율적이다.

```html
<!DOCTYPE html>
<html lang="ko-KR">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>내부 스타일</title>
    **
    <style>
      p {
        color: black;
        background-color: red;
      }
    </style>
    **
  </head>
  <body>
    <p>login</p>
  </body>
</html>
```

### 3. 외부 스타일

- 실무에서 가장 많이 사용하는 방식
- HTML 파일과 CSS 파일을 분리하여 관리
- 유지보수에 용이하고 코드 가독성이 높아짐
- `head` 요소 내부에 css 파일 `href`를 걸어 해당 html 파일과 css 파일을 연결해준다.

```html
<!DOCTYPE html>
<html lang="ko-KR">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>외부 스타일</title>
    **
    <link rel="stylesheet" href="style.css" />
    **
  </head>
  <body>
    <p>Hello world</p>
  </body>
</html>
```

## ☑️ CSS 선택자

<aside>
⚠️ 내용이 너무 많아서 따로 페이지 생성하여 정리해야 할 듯

</aside>

### 전체 선택자(`*`)

### 타입 선택자(태그,요소를 직접 선택)

### 아이디 선택자(`#`)

### 클래스 선택자(`.`)

### 특성 선택자(`[]`)

### 그룹 선택자(`,`)

### 하위 선택자(공백 한 칸)

### 자식 선택자(`>`)

### 일반 형제 선택자(`~`)

### 인접 형제 선택자(`+`)

### 가상 클래스 선택자

### 부정 선택자(`:not`)

## ☑️ CSS Box Model
