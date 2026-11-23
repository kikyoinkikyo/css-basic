# 학습 계획: 대한민국 구석구석 클론코딩으로 배우는 CSS 기초

> 진행 방식: **한 단계 = 클론할 영역 1개 + 새 CSS 개념 1~2개**
> 각 단계가 끝나면 체크리스트를 확인하고, 배운 내용은 `README.md`에 정리하고, 커밋합니다.
>
> - **1부 CSS** (이 문서) → **2부 JavaScript** (`docs/js-plan.md`): 같은 클론코딩을 이어서 움직이게 만들어요.
> - 영역마다 원본 측정값은 `docs/reference/`에 있어요. 영역을 시작할 때 하나씩 만들어요.
> - 색·크기 같은 반복 값은 `css/tokens.css`의 **CSS 변수**를 써요.

## 전체 지도

| 단계 | 클론 영역 | 핵심 개념 | 교재 장 | 상태 |
| --- | --- | --- | --- | --- |
| 0 | 기본 세팅 | 초기화(reset), 웹 폰트, 상속 | 06, 07 | ✅ 완료 |
| 1 | 헤더 배치 | 박스 모델, flex | 08-1 ~ 08-4 | ✅ (보류 2개는 8단계에서) |
| 2 | 헤더 레이어 (언어 선택, 하위 메뉴) | position, z-index | 08-5 | ✅ |
| 3 | 히어로 영역 (사진 카드) | overflow, object-fit, position 복습, **CSS 변수** | 08, 09 | 🔄 진행 중 |
| 4 | 빠른 메뉴, 카드 목록 | flex-wrap, gap, aspect-ratio, 말줄임 | 08, 09 | ⬜ |
| 5 | 메뉴/카드의 상태 표현 | 고급 선택자, 가상 클래스·가상 요소, 상태 클래스, 숨김 텍스트 | 10 | ⬜ |
| 6 | 움직임 | transition, transform, animation | 11 | ⬜ |
| 7 | 모바일 화면 | 미디어 쿼리, 반응형, 상대 단위(rem·vw), clamp() | 12 | ⬜ |
| 8 | 푸터 + 마무리 | 총복습, CSS 파일 구조 정리 | 전체 | ⬜ |
| ➡️ | **2부 JavaScript** | `docs/js-plan.md` | — | ⬜ |

---

## 0단계: 기본 세팅 ✅

**이미 한 것**: `reset` 작성, Pretendard 웹 폰트 연결, `a`·`button` 기본 모양 제거

스스로 확인하기
- [ ] `* { box-sizing: border-box; }`를 왜 넣었는지 설명할 수 있다.
- [ ] `color: inherit`의 뜻(부모 값을 물려받기)을 설명할 수 있다.

📖 [box-sizing](https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing) · [inherit](https://developer.mozilla.org/ko/docs/Web/CSS/inherit) · [상속](https://developer.mozilla.org/ko/docs/Web/CSS/Inheritance)

---

## 1단계: 헤더 배치 — 박스 모델과 flex ✅

**목표**: 로고 · 메뉴 · 유틸 아이콘을 한 줄에 놓고, 가운데 영역의 최대 너비를 정하기

체크리스트
- [x] `.inner`에 `max-width`와 `margin: 0 auto`로 가운데 정렬하기
- [x] `display: flex`로 세 덩어리를 가로로 나란히 놓기
- [x] 메뉴 글자의 위아래 가운데를 맞추고, 메뉴를 누를 수 있는 영역을 헤더 높이만큼 채우기
- [ ] 원본 사이트와 간격(gap, padding)을 개발자 도구로 비교해 맞추기 ⏸️ 보류 (8단계 마무리 때 함께)
- [ ] 연습용 배경색(aquamarine, thistle 등)을 지우고 원본 색으로 바꾸기 ⏸️ 보류 (8단계 마무리 때 함께)

스스로 확인하기
- [ ] **flex container**(부모)와 **flex item**(자식)이 각각 어떤 요소인지 짚을 수 있다.
- [ ] `justify-content`와 `align-items`가 각각 어느 방향의 정렬인지 설명할 수 있다.
- [ ] `margin`과 `padding`의 차이를 화면에서 구분할 수 있다.

📖 [flexbox 기본 개념](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox) · [justify-content](https://developer.mozilla.org/ko/docs/Web/CSS/justify-content) · [align-items](https://developer.mozilla.org/ko/docs/Web/CSS/align-items) · [gap](https://developer.mozilla.org/ko/docs/Web/CSS/gap)

---

## 2단계: 헤더 레이어 — position ✅

**목표**: 언어 선택 목록, 하위 메뉴(depth2)처럼 **문서 흐름에서 제외되어 다른 요소 위에 겹쳐 배치되는 상자** 만들기

체크리스트
- [x] `.language-layer`에 `position: absolute` 적용해 보기
- [ ] `relative`를 **어느 요소에** 줘야 레이어 위치의 기준이 되는지 실험하기 ⏭️ 건너뜀
      (지금 CSS에 주석 처리된 `position: relative`들을 하나씩 켜 보고 차이 관찰하기)
- [x] 하위 메뉴(`.depth2-wrap`)를 헤더 바로 아래, 화면 전체 너비로 펼치기 (지금은 `display: none`)
- [x] 레이어가 다른 콘텐츠에 가려지면 `z-index`로 해결하기
- [x] `README.md`의 비어 있는 **08-5 position** 항목 정리하기

스스로 확인하기
- [ ] `static` / `relative` / `absolute` / `fixed` / `sticky`의 차이를 한 줄씩 말할 수 있다.
- [ ] "absolute는 **가장 가까운, position이 지정된 조상**을 기준으로 한다"는 말을 내 코드로 설명할 수 있다.

📖 [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) · [z-index](https://developer.mozilla.org/ko/docs/Web/CSS/z-index) · [포함 블록(containing block)](https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block)

---

## 3단계: 히어로 영역 — 사진 카드 🔄

> ⚠️ 원본 사이트의 히어로가 바뀌었어요. **지금 사이트 기준**으로 다시 만들어요. 측정값은 `docs/reference/hero.md`에 있어요.

**목표**: 큰 사진 카드 위에 제목·부제목·버튼을 겹쳐 놓고, 양옆 카드가 조금씩 보이게 하기 (슬라이드 동작은 하지 않고 정지 화면만)

체크리스트
- [x] 예전 히어로 HTML을 지금 사이트 구조로 다시 작성하기 — Claude 작성
- [x] 히어로 HTML에 케밥 케이스 클래스 이름 붙이기
- [x] 카드 1장 만들기: 크기, 둥근 모서리, `overflow: hidden`
- [x] 사진이 찌그러지지 않게 `object-fit`으로 채우기
- [x] 글자 묶음을 카드 왼쪽 아래에 `position: absolute`로 배치하기
- [x] 제목·부제목·"자세히 보기" 꾸미기 (반투명 rgba 색) + 아이콘 SVG 흰색·회전 (transform 맛보기)
- [x] 이전·다음 원형 버튼 (원형, 반투명 배경, 흰 화살표, 회전, 선 굵기)
- [ ] "1 / 10" 숫자와 일시정지 버튼 꾸미기 (위치는 Swiper 배치와 함께)
- [ ] **CSS 변수**: 히어로 CSS의 색·글자 크기·모서리 값을 `css/tokens.css` 변수(`var(--이름)`)로 바꾸기
- [ ] **CSS 변수**: 히어로에서만 쓰는 값(카드 940 × 626, 글자 묶음 630px)은 `.sw-hero` 안에 변수로 만들기
- [ ] 카드 3장을 가로로 놓고, 양옆 카드는 일부만 보이게 자르기 ⏸️ 보류 (Swiper 설정으로 처리)

스스로 확인하기
- [ ] `overflow: hidden`이 둥근 모서리에서 하는 역할을 설명할 수 있다.
- [ ] `object-fit`의 `cover`와 `contain`의 차이를 설명할 수 있다.
- [ ] 값을 직접 쓰는 것(하드코딩)과 변수를 쓰는 것의 차이를 말할 수 있다.

📖 [CSS 변수 사용하기](https://developer.mozilla.org/ko/docs/Web/CSS/Using_CSS_custom_properties) · [var()](https://developer.mozilla.org/ko/docs/Web/CSS/var) · [overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow) · [object-fit](https://developer.mozilla.org/ko/docs/Web/CSS/object-fit) · [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) · [position](https://developer.mozilla.org/ko/docs/Web/CSS/position)

---

## 4단계: 빠른 메뉴와 카드 목록

**목표**: 아이콘 메뉴, 여행 코스·축제·이벤트 카드처럼 **같은 모양이 반복되는 목록** 만들기

체크리스트
- [ ] 카드 1개를 먼저 완성한 다음, 여러 개로 늘리기
- [ ] `flex-wrap`과 `gap`으로 줄바꿈과 간격 맞추기
- [ ] 제목이 길면 말줄임표(…)로 자르기
- [ ] 카드 모서리 둥글게, 그림자 넣기
- [ ] `aspect-ratio`로 사진 비율(예: 4:3) 고정하기
- [ ] 두 줄 넘는 글은 말줄임(`-webkit-line-clamp`) 해 보기

스스로 확인하기
- [ ] 같은 클래스를 여러 카드에 재사용하면 무엇이 편한지 말할 수 있다.

📖 [flex-wrap](https://developer.mozilla.org/ko/docs/Web/CSS/flex-wrap) · [text-overflow](https://developer.mozilla.org/ko/docs/Web/CSS/text-overflow) · [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) · [box-shadow](https://developer.mozilla.org/ko/docs/Web/CSS/box-shadow) · [aspect-ratio](https://developer.mozilla.org/ko/docs/Web/CSS/aspect-ratio)

---

## 5단계: 상태 표현 — 고급 선택자

**목표**: 마우스를 올리면 하위 메뉴가 열리고, 카드·버튼 모양이 바뀌게 하기

체크리스트
- [ ] `:hover`로 메뉴에 마우스를 올리면 depth2 보이기
- [ ] 키보드(Tab) 사용자를 위해 `:focus-visible`, `:focus-within` 써 보기
- [ ] 자식 선택자(`>`), 하위 선택자(띄어쓰기)의 차이 실험하기
- [ ] `::before` / `::after`로 장식 요소(구분선, 아이콘 등) 만들기
- [ ] `:nth-child()`로 특정 순서의 항목만 꾸미기
- [ ] **상태 클래스**: 열림 상태를 `is-open` 클래스로 표현하기 (JS 단계 준비, `docs/js-plan.md` 참고)
- [ ] **숨김 텍스트**: 화면에는 안 보이고 화면 낭독기만 읽는 제목 만들기 (흔히 `.blind`라고 불러요)
- [ ] 선택자를 짧게 정리하기: 4~5단계로 긴 선택자(`.a .b c d`)를 줄이고 명시도 비교하기

스스로 확인하기
- [ ] 가상 **클래스**(`:`)와 가상 **요소**(`::`)의 차이를 말할 수 있다.
- [ ] 선택자가 여러 개 겹칠 때 어느 스타일이 이기는지(명시도) 판단할 수 있다.

📖 [:hover](https://developer.mozilla.org/ko/docs/Web/CSS/:hover) · [:focus-within](https://developer.mozilla.org/ko/docs/Web/CSS/:focus-within) · [자식 결합자](https://developer.mozilla.org/ko/docs/Web/CSS/Child_combinator) · [::before](https://developer.mozilla.org/ko/docs/Web/CSS/::before) · [:nth-child()](https://developer.mozilla.org/ko/docs/Web/CSS/:nth-child) · [명시도](https://developer.mozilla.org/ko/docs/Web/CSS/Specificity)

---

## 6단계: 움직임 — 트랜지션과 애니메이션

**목표**: 바뀌는 순간을 부드럽게 만들기

체크리스트
- [ ] 메뉴·버튼 색이 천천히 바뀌게 `transition` 넣기
- [ ] 카드에 마우스를 올리면 이미지가 살짝 커지게 `transform: scale()` 쓰기
- [ ] 진행 막대(progress bar)를 `@keyframes` 애니메이션으로 채워 보기
- [ ] 움직임을 줄여 달라고 설정한 사용자를 위해 `prefers-reduced-motion` 적용하기

📖 [transition](https://developer.mozilla.org/ko/docs/Web/CSS/transition) · [transform](https://developer.mozilla.org/ko/docs/Web/CSS/transform) · [animation](https://developer.mozilla.org/ko/docs/Web/CSS/animation) · [@keyframes](https://developer.mozilla.org/ko/docs/Web/CSS/@keyframes)

---

## 7단계: 모바일 화면 — 반응형

**목표**: 화면이 좁아지면 배치가 바뀌게 하기

체크리스트
- [ ] 개발자 도구의 기기 모드(Ctrl+Shift+M)로 원본 사이트가 언제 바뀌는지 관찰하기
- [ ] `@media`로 좁은 화면에서는 메뉴를 숨기고 다른 버튼 보이기
- [ ] 빠른 메뉴를 모바일에서 가로로 스크롤되게 하기 (HTML 주석 참고)
- [ ] 상대 단위 `rem`, `vw`, `%`와 `px`의 차이 실험하기
- [ ] `clamp()`로 화면 크기에 따라 글자 크기가 자연스럽게 바뀌게 하기
- [ ] 브레이크포인트(화면 너비 기준값)를 정해서 기록하기

📖 [@media](https://developer.mozilla.org/ko/docs/Web/CSS/@media) · [미디어 쿼리 사용하기](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_media_queries/Using_media_queries) · [overflow-x](https://developer.mozilla.org/ko/docs/Web/CSS/overflow-x) · [rem 등 길이 단위](https://developer.mozilla.org/ko/docs/Web/CSS/length) · [clamp()](https://developer.mozilla.org/ko/docs/Web/CSS/clamp) · [prefers-reduced-motion](https://developer.mozilla.org/ko/docs/Web/CSS/@media/prefers-reduced-motion)

---

## 8단계: 푸터 + 마무리

- [ ] 푸터를 **힌트 없이** 혼자 만들어 보기 (지금까지 배운 것 총복습)
- [ ] 연습용 배경색 모두 지우기
- [ ] 원본과 나란히 띄워 놓고 다른 점 목록 만들기 → 하나씩 고치기
- [ ] `README.md`의 09~12장 정리 완성하기
- [ ] **CSS 파일 구조 정리**: `clone-exercise.css` 맨 위의 초기화 코드와 `reset.css`가 겹치는 부분 정리하기
- [ ] **하드코딩 점검**: 남아 있는 색·크기 값을 찾아 `tokens.css` 변수로 바꾸기
- [ ] 2부 JavaScript를 시작하기 전에 `docs/js-plan.md`의 "지금부터 지켜 두면 좋은 약속" 점검하기

---

## 덧붙임: 교재 범위 밖이지만 알아 두면 좋은 것

- **grid**: 2차원(가로+세로) 배치 도구예요. 교재 범위 밖이라 이 과정에서는 flex로 만들어요. 다 마친 뒤 카드 목록을 grid로 바꿔 보면 좋은 연습이 돼요. 📖 [grid](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_grid_layout)
- **외부 라이브러리 CSS 덮어쓰기**: Swiper를 연결하면 Swiper의 CSS가 먼저 적용돼요. 내 CSS를 **나중에** 연결해서 덮어써요. (2부 J3)
