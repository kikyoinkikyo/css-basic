# 학습 계획: 대한민국 구석구석 클론코딩으로 배우는 CSS 기초

> 진행 방식: **한 단계 = 클론할 영역 1개 + 새 CSS 개념 1~2개**
> 각 단계가 끝나면 체크리스트를 확인하고, 배운 내용은 `README.md`에 정리하고, 커밋합니다.

## 전체 지도

| 단계 | 클론 영역                          | 핵심 개념                          | 교재 장     | 상태       |
| ---- | ---------------------------------- | ---------------------------------- | ----------- | ---------- |
| 0    | 기본 세팅                          | 초기화(reset), 웹 폰트, 상속       | 06, 07      | ✅ 완료    |
| 1    | 헤더 배치                          | 박스 모델, flex                    | 08-1 ~ 08-4 | 🔄 진행 중 |
| 2    | 헤더 레이어 (언어 선택, 하위 메뉴) | position, z-index                  | 08-5        | 🔄 시작함  |
| 3    | 히어로 영역                        | 배경 이미지, 그라데이션            | 09          | ⬜         |
| 4    | 빠른 메뉴, 카드 목록               | flex-wrap, gap, 이미지 크기 맞추기 | 08, 09      | ⬜         |
| 5    | 메뉴/카드의 상태 표현              | 고급 선택자, 가상 클래스·가상 요소 | 10          | ⬜         |
| 6    | 움직임                             | transition, transform, animation   | 11          | ⬜         |
| 7    | 모바일 화면                        | 미디어 쿼리, 반응형                | 12          | ⬜         |
| 8    | 푸터 + 마무리                      | 지금까지 배운 것 총복습            | 전체        | ⬜         |

---

## 0단계: 기본 세팅 ✅

**이미 한 것**: `reset` 작성, Pretendard 웹 폰트 연결, `a`·`button` 기본 모양 제거

스스로 확인하기

- [ ] `* { box-sizing: border-box; }`를 왜 넣었는지 설명할 수 있다.
- [ ] `color: inherit`의 뜻(부모 값을 물려받기)을 설명할 수 있다.

📖 [box-sizing](https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing) · [inherit](https://developer.mozilla.org/ko/docs/Web/CSS/inherit) · [상속](https://developer.mozilla.org/ko/docs/Web/CSS/Inheritance)

---

## 1단계: 헤더 배치 — 박스 모델과 flex 🔄

**목표**: 로고 · 메뉴 · 유틸 아이콘을 한 줄에 놓고, 가운데 영역의 최대 너비를 정하기

체크리스트

- [x] `.inner`에 `max-width`와 `margin: 0 auto`로 가운데 정렬하기
- [x] `display: flex`로 세 덩어리를 가로로 나란히 놓기
- [ ] 메뉴 글자의 위아래 가운데를 맞추고, 메뉴를 누를 수 있는 영역을 헤더 높이만큼 채우기
- [ ] 원본 사이트와 간격(gap, padding)을 개발자 도구로 비교해 맞추기
- [ ] 연습용 배경색(aquamarine, thistle 등)을 지우고 원본 색으로 바꾸기

스스로 확인하기

- [ ] **flex container**(부모)와 **flex item**(자식)이 각각 어떤 요소인지 짚을 수 있다.
- [ ] `justify-content`와 `align-items`가 각각 어느 방향의 정렬인지 설명할 수 있다.
- [ ] `margin`과 `padding`의 차이를 화면에서 구분할 수 있다.

📖 [flexbox 기본 개념](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox) · [justify-content](https://developer.mozilla.org/ko/docs/Web/CSS/justify-content) · [align-items](https://developer.mozilla.org/ko/docs/Web/CSS/align-items) · [gap](https://developer.mozilla.org/ko/docs/Web/CSS/gap)

---

## 2단계: 헤더 레이어 — position 🔄

**목표**: 언어 선택 목록, 하위 메뉴(depth2)처럼 **다른 요소 위에 떠 있는 상자** 만들기

체크리스트

- [x] `.language-layer`에 `position: absolute` 적용해 보기
- [ ] `relative`를 **어느 요소에** 줘야 레이어 위치의 기준이 되는지 실험하기
      (지금 CSS에 주석 처리된 `position: relative`들을 하나씩 켜 보고 차이 관찰하기)
- [ ] 하위 메뉴(`.depth2-wrap`)를 헤더 바로 아래, 화면 전체 너비로 펼치기 (지금은 `display: none`)
- [ ] 레이어가 다른 콘텐츠에 가려지면 `z-index`로 해결하기
- [ ] `README.md`의 비어 있는 **08-5 position** 항목 정리하기

스스로 확인하기

- [ ] `static` / `relative` / `absolute` / `fixed` / `sticky`의 차이를 한 줄씩 말할 수 있다.
- [ ] "absolute는 **가장 가까운, position이 지정된 조상**을 기준으로 한다"는 말을 내 코드로 설명할 수 있다.

📖 [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) · [z-index](https://developer.mozilla.org/ko/docs/Web/CSS/z-index) · [포함 블록(containing block)](https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block)

---

## 3단계: 히어로 영역 — 배경과 그라데이션

**목표**: 큰 배경 이미지 위에 제목과 이미지 카드를 겹쳐 놓기 (슬라이드 동작은 하지 않고 첫 장면만)

체크리스트

- [ ] `background-image`, `background-size`, `background-position`으로 배경 깔기
- [ ] 글자가 잘 보이도록 그라데이션을 겹쳐 보기
- [ ] 이미지가 찌그러지지 않게 크기 맞추기

스스로 확인하기

- [ ] `<img>` 태그로 넣는 이미지와 `background-image`의 차이(언제 무엇을 쓰는지)를 말할 수 있다.
- [ ] `background-size`의 `cover`와 `contain`의 차이를 설명할 수 있다.

📖 [background-image](https://developer.mozilla.org/ko/docs/Web/CSS/background-image) · [background-size](https://developer.mozilla.org/ko/docs/Web/CSS/background-size) · [linear-gradient()](https://developer.mozilla.org/ko/docs/Web/CSS/gradient/linear-gradient) · [object-fit](https://developer.mozilla.org/ko/docs/Web/CSS/object-fit)

---

## 4단계: 빠른 메뉴와 카드 목록

**목표**: 아이콘 메뉴, 여행 코스·축제·이벤트 카드처럼 **같은 모양이 반복되는 목록** 만들기

체크리스트

- [ ] 카드 1개를 먼저 완성한 다음, 여러 개로 늘리기
- [ ] `flex-wrap`과 `gap`으로 줄바꿈과 간격 맞추기
- [ ] 제목이 길면 말줄임표(…)로 자르기
- [ ] 카드 모서리 둥글게, 그림자 넣기

스스로 확인하기

- [ ] 같은 클래스를 여러 카드에 재사용하면 무엇이 편한지 말할 수 있다.

📖 [flex-wrap](https://developer.mozilla.org/ko/docs/Web/CSS/flex-wrap) · [text-overflow](https://developer.mozilla.org/ko/docs/Web/CSS/text-overflow) · [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) · [box-shadow](https://developer.mozilla.org/ko/docs/Web/CSS/box-shadow)

---

## 5단계: 상태 표현 — 고급 선택자

**목표**: 마우스를 올리면 하위 메뉴가 열리고, 카드·버튼 모양이 바뀌게 하기

체크리스트

- [ ] `:hover`로 메뉴에 마우스를 올리면 depth2 보이기
- [ ] 키보드(Tab) 사용자를 위해 `:focus-visible`, `:focus-within` 써 보기
- [ ] 자식 선택자(`>`), 하위 선택자(띄어쓰기)의 차이 실험하기
- [ ] `::before` / `::after`로 장식 요소(구분선, 아이콘 등) 만들기
- [ ] `:nth-child()`로 특정 순서의 항목만 꾸미기

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

📖 [transition](https://developer.mozilla.org/ko/docs/Web/CSS/transition) · [transform](https://developer.mozilla.org/ko/docs/Web/CSS/transform) · [animation](https://developer.mozilla.org/ko/docs/Web/CSS/animation) · [@keyframes](https://developer.mozilla.org/ko/docs/Web/CSS/@keyframes)

---

## 7단계: 모바일 화면 — 반응형

**목표**: 화면이 좁아지면 배치가 바뀌게 하기

체크리스트

- [ ] 개발자 도구의 기기 모드(Ctrl+Shift+M)로 원본 사이트가 언제 바뀌는지 관찰하기
- [ ] `@media`로 좁은 화면에서는 메뉴를 숨기고 다른 버튼 보이기
- [ ] 빠른 메뉴를 모바일에서 가로로 스크롤되게 하기 (HTML 주석 참고)

📖 [@media](https://developer.mozilla.org/ko/docs/Web/CSS/@media) · [미디어 쿼리 사용하기](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_media_queries/Using_media_queries) · [overflow-x](https://developer.mozilla.org/ko/docs/Web/CSS/overflow-x)

---

## 8단계: 푸터 + 마무리

- [ ] 푸터를 **힌트 없이** 혼자 만들어 보기 (지금까지 배운 것 총복습)
- [ ] 연습용 배경색 모두 지우기
- [ ] 원본과 나란히 띄워 놓고 다른 점 목록 만들기 → 하나씩 고치기
- [ ] `README.md`의 09~12장 정리 완성하기
