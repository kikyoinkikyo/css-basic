# 06. CSS의 기본

- Cascading Style Sheet
- HTML은 텍스트나 이미지, 표 같은 요소를 웹 문서에 넣어 뼈대를 만드는 역할
- CSS는 텍스트나 이미지, 배경의 크기나 배치 방법 등의 요소의 디자인 담당

## 06-2. 스타일과 스타일 시트

### 스타일 형식

```css
선택자{
속성1: 속성값1;
속성2: 속성값2;
...
}
```

### 스타일 시트

- 스타일 규칙을 한눈에 확인하고
- 필요할 때마다 수정하기 쉽도록 **한군데 묶어 놓은 것**

- 웹 브라우저에 기본으로 만들어져 있는 **브라우저 기본 스타일**
- 사용자 스타일
  - **인라인 스타일**
  - 스타일 시트를 사용하지 않고 적용할 대상에 직접 표시

  ```html
  <p style="color: red">
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed veritatis
    doloremque minima eligendi similique dolore? Odit illum, ducimus minus
  </p>
  ```

  - 내부 스타일 시트
    -html 문서 내부에 head 태그 안에 작성

        ```html
          <style>
          p {
            text-align: center;
            color: blue;
          }
          </style>

         ```

  - **외부 스타일 시트** - 연결 head 태그 안에
    - 여러 웹 문서에서 사용할 스타일을 별도 파일로 저장
    - 필요할 때마다 가져와서 사용
    - 따로 저장해 놓은 스타일 정보를 외부 스타일 시트
    - 확장자는 **.css**

  ```html
  <!-- 외부 스타일 시트 연결 -->
  <link rel="stylesheet" href="css/style.css" />
  ```

  - css/style.css

  ```css
  h1 {
    color: red;
  }
  ```

## 06-3. CSS 기본 선택자

- 선택자는 웹 문서에서 어느 부분에 스타일을 적용할지 알려 주는 것
- 미리 약속되어 있음

### 전체 선택자

- 모든 요소에 적용할 때 사용

```css
*{속성: 값; ...}
```

```css
/* 전체 선택자 */
* {
  margin: 0;
  padding: 0;
}
```

### 타입 선택자 (태그 선택자)

- 특정 태그를 사용한 모든 요소에 스타일 적용
- 브라우저 기본 스타일을 사용자 스타일로 덮어 쓸 때

```css
/* 타입 선택자 */
h3 {
  font-size: 36px;
  color: red;
}
```

### **클래스 선택자**

- 클래스 명으로 요소 선택, 다른 선택자와 구별
- 앞에 '.' 반드시 붙여야함

```css
/* 클래스 선택자 */
.sect-1 {
  background-color: aqua;
}
.sect-2 {
  background-color: aliceblue;
}
.sect-3 {
  background-color: aquamarine;
}
.sect-4 {
  background-color: azure;
}
```

### ** id 선택자 **

- 특정 부분의 한군데만 적용
- id는 중복 사용할 수 없음 한 번만 사용하는 고유한 값
- 요소를 id명으로 선택하기

```css
#아이디명 {
  속성1: 속성1 값;
  속성2: 속성2 값;
}
```

```html
<div id="container"></div>
```

```css
#container {
  width: 500px;
  height: 500px;
  padding: 20px;
  border: 2px solid #000;
  margin: 20px auto;
}
```

### 그룹 선택자

- 여러개 요소를 선택
- 같은 스타일 규칙을 사용

```css
선택자1, 선택자2, 선택자3, ...{스타일 규칙}
```

## 06-4. 스타일 시트

### Cascading 의미

- 스타일 시트에서는 우선순위가 위에서 아래, 즉 계단식으로 적용된다는 의미
- css에서는 웹 요소에 둘 이상의 스타일을 적용할 때 우선순위에 따라 적용할 스타일을 결정
- 스타일 우선순위
  - 스타일 규칙 중요도와 적용 범위에 따라 우선순위 결정
  - 그 우선순위에 따라 위에서 아래로 스타일 적용
- 스타일 상속
  - 태그의 포함 관계에 따라 부모 요소의 스타일을 자식 요소로 위에서 아래로 전달

### 스타일 우선순위

- 중요도
  - 사용자 스타일 > 제작자 스타일 > 브라우저 기본 스타일

- 적용범위
  -!important > 인라인 스타일 > id 스타일 > 클래스 스타일 > 타입 스타일

- 작성 순서
  - 나중에 작성한 스타일이 먼저 작성한 스타일을 덮어씀

### 스타일 상속

- 자식 요소에 별도로 스타일을 지정하지 않으면 부모 요소의 스타일 속성들이 자식 요소로 전달

# 07. 텍스트 스타일

## 07-1. 폰트(글꼴) 속성

- 글자의 모양

### 폰트(글꼴)을 지정. font-family 속성

- 글꼴 지정
- 기본형

```
font-family : 글꼴이름 | 글꼴이름, 글꼴이름,...
```

### font-size

```
font-size: 절대크기 | 상대크기 | 크기 | 백분율
```

- 절대크기: 브라우저에서 지정한 글자 크기
- 상대크기: 부모 요소의 글자 크기를 기준으로 상대적인 글자 크기 지정
- 크기: 브라우저와 상관없이 글자 크기를 직접 지정
- 백분율: 부모 요소의 글자 크기를 기준으로 백분율(%) 표시

- 단위
  - em: 부모 요소에서 지정한 글꼴의 크기를 기준으로 몇 배?
  - rem: 문서 최상단(root)에서 지정한 크기를 기준으로 몇 배?
  - px: 모니터의 1픽셀을 기준으로 1px
  - 그 외 ex, pt

### font-weight

- 글자 굵기
- normal, bold, bolder, lighter
- 100, 200, 300, ..., 900

```
font-weight: 굵기;
```

## 07-2. 웹 폰트 사용

### 웹 폰트 업로드 및 사용

- 설치용 .ttf, .otf
- woff, woff2 eot

```css
@font-face {
  font-family: "Akaya Kanadaka", system-ui;
  src: url("../assets/fonts/AkayaKanadaka-Regular.ttf");
}

h1 {
  font-family: "Akaya Kanadaka", system-ui;
  font-weight: 400;
  font-style: normal;
  font-size: 48px;
}
```

## 07-3. 텍스트 관련 스타일 속성

### color

```css
선택자 {
  color: 색상;
}
```

- 16진수 Hex code: #ff6600, #f60
- rgb, rgba: rgb(255, 255, 255), rgba(0, 0, 0, 0.5)
- hsl, hsla: hsl(60, 100%, 50%), hsla(0, 100%, 50%, 0.80)

### text-align

- 텍스트 정렬
- start: 현재 텍스트 줄의 시작 위치에 맞춰 문단 정렬
- end: 현재 텍스트 줄의 끝 위치에 맞춰 문단 정렬
- left: 왼쪽 정렬
- right: 오른쪽 정렬
- **center**: 가운데 정렬
- justify: 양쪽 정렬
- match-parent: 부모 요소를 따라 문단을 정렬

### line-height

- 행간(줄 간격)
- px, 백분율, %

### text-decoration

- underline(밑줄), line-through(취소선), overline(윗줄), none(없음)

### text-shadow

- text-shadow: x축 y축 blur값 색상값(hex, rgb, rgba, hsl, hsla)

### text-transform

- 영문자 표기할 때 대소 문자를 원하는대로 변경
- none: 기본값
- capitalize: 첫 번째 글자를 대문자로 변환
- uppercase: 모든 글자 대문자 변환
- lowercase: 모든 글자 소문자 변환
- full-width: 가능한 한 모든 문자를 전각 문자로 변환

```css
선택자 {
  text-transform: uppercase;
}
```

### letter-spacing, word-spacing

- letter-spacing: 자간(글자 사이의 간격)
- word-spacing: 단어와 단어 사이 간격(잘 안씀)

## 07-4. 목록 스타일

### list-style-type

- bullet 모양, 번호 스타일 지정
  - disc: • 채운 원 모양
  - circle: 빈 원 모양
  - sqaure: 채운 사각형
  - decimal: 1, 2, 3, 4, ... 10진수
  - decimal-leading-zero: 01, 02, 03, 04, ...
  - lower-roman: 소문자 로마자
  - upper-roman: 대문자 로마자
  - lower-alpha 또는 lower-latin: a, b, c, d, ...
  - upper-alpha 또는 upper-latin: A, B, C, D, ...
  - none: 없음

### list-style-image

- bullet을 원하는 이미지로

```css
ul {
  list-style-image: url("이미지 경로");
}
```

### list-style-position

- bullet이나 번호의 위치를 들여쓰기

```
list-style-position: inside(들여쓰기) | outside(기본값);
```

### list-style

- list-style-type, image, position 한꺼번에 표시

```css
ul {
  /* list-stlye: lower-alpha inside; */
  list-style: none;
}
```

## 07-5. 표 스타일

- 개인적으로 알아보실 분만 알아보기

# 08. **레이아웃과 CSS 박스모델**

- 웹 문서에서 내용을 배치할 때는 각 요소를 박스 형태로 구성
- 이것을 css 박스 모델이라고 함
- 여백(margin), 안쪽여백(padding), 테두리(border), 콘텐츠 영역으로 구성

## 08-1. 박스 모델

### 블록 레벨 요소와 인라인 레벨 요소

- 블록 레벨인지 인라인 레벨 요소인지에 따라 요소를 나열하는 방법이 달라진다
- 블록 레벨 요소: 혼자 한 줄 전부 차지, 너비가 100%
  - div, h1, p, 등
- 인라인 레벨 요소: 한 줄을 다 차지하지 않고, 콘텐츠만큼만 영역 차지
  - span, img, strong, a, 등

### 콘텐츠 영역, padding, border, margin

### width, height

- 너비, 높이
- 크기: px, em, rem 단위로 지정
- 백분율: 부모 요소를 기준으로 % 지정
- auto: 콘텐츠 양에 따라 자동으로 결정, 기본값

### box-sizing

- border-box: 테두리를 포함한 너비, 높이
- content-box: 테두리를 포함하지 않은 콘텐츠 영역 만큼만, 기본값

### box-shadow

- x축: 수평거리, 왼쪽은 -, 오른쪽은 +
- y축: 수직거리, 위쪽은 -, 오른쪽은 +
- 흐림정도: 값이 커질 수록 부드러운 그림자 표시
- 퍼짐정도: 그림자 크기
- 색상: 기본값은 검정색
- inset: inner shadow 안쪽 그림자로 표시

## 08-2. 테두리 스타일

### 박스 모델의 방향

- 4개의 방향: top - right - bottom - left
- 3개의 방향: top - left/right - bottom
- 2개의 방향: top/bottom - left/right
- 1개의 방향: top/left/bottom/right

### border-style

- none(기본값)
- hidden: 테두리 숨기기
- **solid**: 실선
- dotted: 점선
- dashed: 짧은 직선
- double: 이중선
- groove: 홈이 파인 듯 입체 느낌
- inset
- outset
- ridge

### border-width

- 테두리 두께

### border-color

- 테두리 색상

### border

- 테두리 스타일을 묶어 지정

```css
.box {
  width: 500px;
  height: 500px;
  margin: 50px auto;
  border-style: solid;
  border-width: 8px 24px 16px 32px;
  border-color: rgba(255, 30, 30, 0.678);

  border: 4px solid rgba(255, 30, 30, 0.678);
}
```

### border-radius

- 모서리 둥글게, 테두리 둥글게
- 크기, 백분율(만약 값이 50%: 정사각형일떄 - 정원, 직사각형일때 - 타원)
- 방향 top/left - top/right - bottom/right - bottom/left

```css
.box {
  width: 500px;
  height: 500px;
  margin: 50px auto;
  /* border-style: solid; */
  /* border-width: 8px 24px 16px 32px; */
  /* border-color: rgba(255, 30, 30, 0.678); */
  border: 4px solid rgba(255, 30, 30, 0.678);
  /* border-radius: 50% */
  border-radius: 50px;
  border-top-left-radius: 400px;
}
```

## 08-3. 여백

- 4개의 방향: top - right - bottom - left
- 3개의 방향: top - left/right - bottom
- 2개의 방향: top/bottom - left/right
- 1개의 방향: top/left/bottom/right

### margin

- 요소 주변 여백
- px, rem, em, %, auto

```
*상하 여백 50px, 좌우 여백 auto(자동) - 요소가 가운데*
margin: 50px auto;
```

### margin 중첩 현상

- 세로로 배치할 경우 각 요소의 마진과 마진이 서로 만나면 큰 쪽으로 겹쳐지는 문제

```css
.box-1 {
  width: 300px;
  height: 300px;
  border: 4px solid #000;
  margin: 50px auto;
}

.box-2 {
  width: 300px;
  height: 300px;
  border: 4px solid #000;
  margin: 30px auto;
}
```

### padding

- 안쪽 여백
- 콘텐츠와 박스 사이 여백

```css
.box-1 {
  width: 300px;
  height: 300px;
  border: 4px solid #000;
  margin: 50px auto;
  padding: 16px;
}

.box-2 {
  width: 300px;
  height: 300px;
  border: 4px solid #000;
  margin: 30px auto;
  padding: 32px;
}
```

## 08-4. 레이아웃 만들기

### display

- block: 블록 레벨 요소로 만든다.
- inline: 인라인 레벨 요소로 만든다.
- inline-block: 인라인 레벨 요소와 블록 레벨 요소의 속성을 모두 가지고 있음
- none: 화면에 표시하지 않음
- **flex: flex박스**

```css
ul,
li {
  list-style: none;
}

ul {
  margin: 20px auto;
  padding: 16px;
  border: 1px solid #000;
}

li {
  display: inline-block;
  border: 1px solid #000;
  padding: 8px;
  margin: 16px;
}
```

### float

- 요소를 문서 위에 떠 있게 만든다.
  - left: 해당 요소를 문서의 왼쪽에 배치
  - right: 해당 요소를 문서의 오른쪽에 배치
  - none: 기본값

### float 속성 해제 clear

- float 속성이 더 이상 유효하지 않다고 알려줌
  - left: float : left를 해제
  - right: float: right를 해제
  - both: left, right 둘다 해제

```css
img {
  float: left;
  margin-right: 40px;
  width: 800px;
  height: 800px;
}

p {
  margin-top: 16px;
}
.bottom-text {
  clear: both;
}
```

```css
div {
  width: 100px;
  height: 100px;
}

.box-1 {
  background-color: aqua;
  float: left;
  margin-top: 20px;
  margin-right: 20px;
}
.box-2 {
  background-color: yellowgreen;
  float: left;
  margin-top: 20px;
}
.box-3 {
  background-color: violet;
  width: 100%;
  margin-top: 20px;
}
.box-4 {
  background-color: burlywood;
  clear: both;
  margin-top: 32px;
  width: 100%;
}
```

### **display: flex; flex 박스 **

#### 용어 정리

- flex container (부모 박스) : 플렉스 박스 레이아웃을 적용할 flex item을 묶는 요소
- flex item (자식 박스)
- main axis (주축)
- cross axis (교차축)

#### flex item(자식 박스)을 배치 하는 flex container(부모 박스)의 속성

- **justify-content: 주축의 정렬 방법**
- **align-items: 교차축의 정렬 방법**
- align-self: 교차축에 있는 개별 flex item의 정렬 방법
- align-content: 교차축에서 여러 줄로 표시된 항목의 정렬 방법

- _display 속성_
  - **flex**: 컨테이너 안의 flex item을 블록 레벨 요소로 배치(새 줄애서 시작, 부모 너비를 100% 채움)
  - inline-flex: 컨테이너가 inline-block처럼 동작 (옆으로 나란히 배치, 내용만큼만 너비 차지)

- _플렉스 주축과 방향을 지정하는 flex-direction_
  - row(기본값)
  - row-reverse
  - column
  - column-reverse

- _flex item의 줄을 바꾸는 flex-wrap_
  - nowrap(기본값)
  - wrap
  - wrap-reverse

- _주축 정렬 방법 justify-content_
  - flex-start: 주축의 시작점
  - flex-end: 주축의 끝점
  - center: 주축의 중앙
  - space-between: 첫 번째 항목과 끝 항목을 주축의 시작점과 끝점에 배치 후 나머지는 그 사이에 균등하게 배치
  - space-around: 모든 항목을 주축에 균등하게 배치

_교차축 정렬 방법 align-items_

- flex-start: 교차축 시작점
- flex-end: 교차축 끝점
- center: 교차축 중앙
- baseline: 교차축의 문자 기준선에 맞춰 배치
- stretch: flex item을 늘려 교차축에 가득 차게 배치

- _여러 줄일 때 교차축 정렬 방법 align-content_
  - flex-start:
  - flex-end:
  - center:
  - space-between:
  - space-around:
  - stertch:

#### flex item(자식 박스)의 속성

- _align-self_
- 특정 항목만 지정
- flex-start
- flex-end
- center
- stretch

## 08-5. 웹 요소 위치 지정 position

- 요소를 원하는 위치에 배치하는 속성
- `top`, `right`, `bottom`, `left`와 함께 사용

### position 값

- static: 기본값, 문서 흐름대로 배치 (top/left 등이 적용되지 않음)
- **relative**: 원래 자리를 기준으로 이동, 원래 자리는 그대로 차지함
- **absolute**: 문서 흐름에서 빠져나와 떠 있는 상자가 됨, 기준 상자를 기준으로 배치
- fixed: 화면(브라우저 창)을 기준으로 고정, 스크롤해도 그 자리에 있음
- sticky: 평소엔 제자리에 있다가 스크롤로 정해진 위치에 닿으면 달라붙음

### top, right, bottom, left

- 기준점에서 얼마나 떨어질지 지정
- px, %, auto 등
- `top: 100%` → 기준 상자 높이만큼 아래 = 기준 상자의 **바로 아래**

### absolute의 기준 상자 찾기

- 부모 → 그 부모 → ... 순서로 올라가면서
- **position이 static이 아닌 가장 가까운 조상**을 기준으로 삼음
- 그런 조상이 하나도 없으면 문서 전체(최상위)가 기준
- 그래서 보통 기준이 될 부모에 `position: relative`를 줌

### z-index

- 요소가 겹칠 때 쌓이는 순서
- 숫자가 클수록 위에 표시
- position이 static이 아닌 요소에 적용 (flex 자식 요소에도 적용됨)

### 클론코딩 예시: 하위 메뉴를 헤더 바로 아래 전체 너비로

```css
.header {
  position: relative; /* 기준 상자 */
  height: 90px;
}

.depth2-wrap {
  position: absolute;
  top: 100%; /* 헤더 바로 아래 */
  left: 0;
  width: 100%; /* 헤더 전체 너비 */
  z-index: 1; /* 메인 콘텐츠보다 위 */
}
```

- `.header`와 `.depth2-wrap` 사이의 상자(`.inner`, `.nav`, `li` 등)에 relative를 주면 기준이 바뀌니 주의!

# 09. 이미지, 그라데이션, 배경

# 10. css 고급 선택자

# 11. 트랜지션, 에니메이션

# 12. 반응형, 미디어 쿼리

# 부록 A. CSS 변수 (교재 범위 밖)

## A-1. CSS 변수란?

- 반복되는 값(색, 글자 크기, 모서리, 간격 등)에 **이름을 붙여 두고** 꺼내 쓰는 것
- 정식 이름은 **사용자 지정 속성 (custom properties)**
- 이렇게 이름 붙인 디자인 값을 **디자인 토큰**이라고 부름
- 비유: 전화번호(`#fff`)를 외우지 않고 연락처 이름(`--color-white`)으로 저장해 두기

```css
/* 만들기: 이름은 반드시 -- 로 시작 */
선택자 {
  --변수이름: 값;
}

/* 꺼내 쓰기: var( ) 로 감싸기 */
선택자 {
  속성: var(--변수이름);
}
```

## A-2. 전역 변수와 지역 변수

- CSS 변수는 **만든 요소와 그 자손**만 쓸 수 있음 (일반 속성처럼 **상속**됨)

| 어디에 만드나                     | 누가 쓸 수 있나        | 이름      |
| --------------------------------- | ---------------------- | --------- |
| `:root` (= 문서 맨 꼭대기 `html`) | 페이지의 **모든 요소** | 전역 토큰 |
| `.sw-hero` 같은 영역 선택자       | 그 영역과 안쪽 요소만  | 지역 변수 |

- 나누는 기준
  - **여러 영역**에서 쓰는 값, 디자인 **규칙** → 전역 (`css/tokens.css`)
    - 예: 흰색, 14px 글자, 카드 모서리 12px
  - **한 영역**에서만 쓰는 치수 → 지역 (그 영역 선택자 안)
    - 예: 히어로 카드 940 × 626

```css
/* tokens.css — 전역 토큰 */
:root {
  --color-white: #fff;
  --radius-lg: 12px;
}

/* 지역 변수 예시 */
.card-area {
  --card-w: 300px;
}
.card-area .card {
  width: var(--card-w);
  border-radius: var(--radius-lg);
}
```

## A-3. 왜 쓰나? (하드코딩과 비교)

- **하드코딩**: 값을 코드에 직접 쓰는 것 (예: `color: #fff;`)

|              | 하드코딩 `#fff`                      | 변수 `var(--color-white)`                |
| ------------ | ------------------------------------ | ---------------------------------------- |
| 값을 바꿀 때 | 쓴 곳을 **전부** 찾아서 고침         | `tokens.css` **한 줄**만 고침            |
| 읽을 때      | `rgba(0,0,0,.4)`가 왜 이 값인지 모름 | `--color-black-40` 이름으로 알 수 있음   |
| 실수         | 곳곳에 비슷하지만 다른 값이 섞임     | 모두 같은 값                             |
| 나중에       | -                                    | 다크 모드, JavaScript로 값 바꾸기가 쉬움 |

## A-4. 주의할 점

- **이름이 틀리면 조용히 무시됨**: 오류 없이 그 줄만 적용 안 됨 → 개발자 도구로 확인
  - Styles 패널에서 `var(--이름)`에 마우스를 올리면 실제 값이 보임
- **대신할 값(fallback)**: 변수가 없을 때 뒤의 값을 사용

```css
color: var(--color-point, #ff6600);
```

- **이름 규칙**: `--분류-역할` (케밥 케이스)
  - 예: `--color-text`, `--fs-sm`, `--radius-lg`, `--space-4`
  - 값(`--white-fff`)보다 **역할**로 지어야 값이 바뀌어도 이름이 어색하지 않음
- 이 프로젝트에서는 `css/tokens.css`를 다른 CSS보다 **먼저** 연결함

```html
<link rel="stylesheet" href="css/reset.css" />
<link rel="stylesheet" href="css/tokens.css" />
<link rel="stylesheet" href="css/clone-exercise.css" />
```

- 참고: [MDN CSS 변수 사용하기](https://developer.mozilla.org/ko/docs/Web/CSS/Using_CSS_custom_properties) · [var()](https://developer.mozilla.org/ko/docs/Web/CSS/var) · [:root](https://developer.mozilla.org/ko/docs/Web/CSS/:root)
