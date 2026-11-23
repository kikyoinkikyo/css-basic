# 히어로 영역 참고 자료 (2026-11-20 원본 사이트 기준)

> 원본 사이트를 브라우저 화면 너비 1864px에서 열고, 개발자 도구로 **실제로 측정한 값**이에요.
> 원본 사이트는 내용이 자주 바뀌니, 다르게 보이면 개발자 도구로 다시 확인하세요.

## 생김새

```
┌──────┐ ┌──────────────────────────────┐ ┌──────┐
│ 이전  │ │        큰 사진 (카드)          │ │ 다음  │
│ 카드  │(<)                            (>) 카드  │
│ 일부  │ │ 제목 (2줄, 굵게, 흰색)         │ │ 일부  │
│      │ │ 부제목 (흐린 흰색)             │ │      │
│      │ │ [자세히 보기 >]       2 / 10 ⏸ │ │      │
└──────┘ └──────────────────────────────┘ └──────┘
```

- 가운데 큰 카드 1장 + 양옆 카드가 **조금씩** 보이는 모양이에요.
- 슬라이드는 모두 10장이에요. (넘기는 동작은 JavaScript라서 우리는 **정지 화면**만 만들어요.)
- 예전에 만든 HTML 구조(캠페인 이름, 날짜, 버튼 2개, 작은 이미지 슬라이드)는 **지금 사이트에 없어요.**

## 원본 구조 (클래스 이름은 원본 그대로)

```
div.main_showcase_area            ← 히어로 전체
└ div.swiper                      ← 슬라이드 묶음
  ├ div.swiper-wrapper            ← 카드들을 가로로 나열
  │ └ div.swiper-slide (×10)      ← 카드 1장
  │   ├ span.img > img            ← 사진
  │   └ a                         ← 글자 묶음 (링크)
  │     ├ strong                  ← 제목
  │     ├ em                      ← 부제목
  │     └ span.view               ← "자세히 보기 >" 버튼 모양
  ├ div.nav_btn                   ← 이전 / 다음 화살표 버튼
  └ div.page_btn                  ← "2 / 10" 숫자 + 일시정지 버튼
```

> 우리 프로젝트는 **케밥 케이스**를 쓰니, 클래스 이름은 직접 바꿔서 지어요. (예: `hero`, `hero-slide` …)

## 측정값

| 요소 | 속성 | 값 |
| --- | --- | --- |
| 카드 1장 | width × height | 940px × 626px |
|  | 카드 사이 간격 | 16px (오른쪽 margin) |
|  | border-radius | 12px |
|  | overflow | hidden (사진이 둥근 모서리 밖으로 안 나가게) |
|  | position | relative (글자 묶음의 기준 상자) |
| 사진 `img` | 크기 | 카드와 같음 (940 × 626) |
|  | object-fit | cover |
| 글자 묶음 `a` | position | absolute |
|  | left / bottom | 48px / 48px |
|  | width | 630px |
| 제목 `strong` | font-size / weight / line-height | 40px / 800 / 48px |
|  | color | #fff |
| 부제목 `em` | font-size / weight | 20px / 400 |
|  | color | rgba(255, 255, 255, 0.75) |
|  | font-style | normal (em의 기본 기울임을 없앰) |
| "자세히 보기" | display | inline-flex |
|  | font-size / 높이 | 14px / 32px |
|  | padding | 0 16px |
|  | border | 1px solid rgba(255, 255, 255, 0.5) |
|  | border-radius | 2px |
| 이전·다음 버튼 | 크기 | 56px × 56px 원 |
|  | background-color | rgba(0, 0, 0, 0.4) |
| "2 / 10" + 일시정지 | 위치 | 카드 오른쪽 아래 |

## 아이콘 선 굵기 (2026-11-23 원본 CSS에서 확인 · 학생이 개발자 도구로 재확인)

원본도 같은 SVG 파일(`guide_arrow_right24.svg`, `guide_chevron_dw24.svg`)을 쓰지만, **CSS의 `stroke-width`로 굵기를 덮어써요.** SVG 파일 안의 `stroke-width="1.6"`은 그대로 쓰이지 않아요.

| 아이콘 | 실제로 이기는 원본 규칙 | 값 | 우리 파일 값 |
| --- | --- | --- | --- |
| 이전·다음 화살표 (24 × 24) | `#contents.main_cont_wrap .swiper [class^="swiper-button-"] svg path { stroke-width: 2.5px }` (main.css) | **2.5px** ✅ 개발자 도구로 확인 | 1.6 |
| "자세히 보기" 꺾쇠 (16 × 16) | `[class^="icon_pg"][class*="_sm"] svg path { stroke-width: 0.2rem }` (common.css) | 2px (⬜ 개발자 도구로 재확인 필요) | 1.6 |

> ⚠️ **처음에 1.8px로 잘못 적었어요.** `[class^="icon_pg"][class*="_lg"] svg path { stroke-width: 0.18rem }` 규칙만 보고,
> **id 선택자가 들어간 더 강한 규칙(위 표의 2.5px)**을 놓쳤어요. 같은 요소에 규칙이 여러 개 걸리면 **명시도가 높은 쪽이 이겨요.**
> 그래서 원본 CSS 파일을 읽는 것보다 **개발자 도구의 Computed 값**이 더 정확해요.

- 원본은 `html { font-size: 62.5% }`라서 **1rem = 10px**이에요. (768~1023px 화면에서는 80%)
- `stroke-width`는 SVG 안쪽 좌표(viewBox 24 기준)의 값이라, 아이콘을 16px로 줄이면 선도 같은 비율로 가늘어 보여요.
- 이전 버튼은 원본도 `svg`를 `rotate(180deg)`로 돌려요.

### "자세히 보기" 원본 스타일 (main.css에서 확인)

| 속성 | 원본 값 | 비고 |
| --- | --- | --- |
| `gap` | 0.3rem = **3px** | 학생 측정값과 같음 ✅ |
| `margin-top` | 3.1rem = **31px** | 학생 측정값과 같음 ✅ |
| 아이콘 `span`의 `margin-top` | 0.7rem = 7px | |
| 마우스 올림 | 테두리 색 `#fff` | 5단계 |
| 등장 효과 | `opacity` · `transform` 트랜지션 0.6s | 6단계 |

### 이전·다음 버튼의 나머지 원본 스타일 (같은 날 원본 CSS에서 확인)

| 상태 | 속성 | 값 |
| --- | --- | --- |
| 기본 | `box-shadow` | `1px 1px 6px rgba(26, 26, 26, 0.12)` |
|  | `backdrop-filter` | `blur(5px)` (버튼 뒤 사진을 흐리게) |
| 마우스 올림 (5단계 `:hover`) | `background` | `#fff` |
|  | 화살표 `stroke` | `#3D3D43` |

## 반복되는 값 → 토큰 후보

| 값 | 쓰인 곳 | 토큰 (`css/tokens.css`) |
| --- | --- | --- |
| `#fff` | 제목, 버튼 글자, 아이콘 | `--color-white` |
| `rgba(255, 255, 255, 0.75)` | 부제목 | `--color-white-75` |
| `rgba(255, 255, 255, 0.5)` | "자세히 보기" 테두리 | `--color-white-50` |
| `rgba(0, 0, 0, 0.4)` | 이전·다음 버튼 배경 | `--color-black-40` |
| 40px / 20px / 14px | 제목 / 부제목 / 버튼 글자 | `--fs-display` / `--fs-lg` / `--fs-sm` |
| 800 | 제목 굵기 | `--fw-extrabold` |
| 12px / 2px | 카드 / 작은 버튼 모서리 | `--radius-lg` / `--radius-sm` |
| 48px | 글자 묶음 left · bottom | `--space-12` |
| 56px / 24px / 16px | 원형 버튼 / 큰 아이콘 / 작은 아이콘 | `--btn-icon-lg` / `--icon-md` / `--icon-sm` |
| 940 × 626, 630px | 히어로 카드 크기, 글자 묶음 너비 | **히어로 전용** → `.sw-hero` 안에서 변수로 |

## 움직임 (JavaScript 단계에서 사용)

2026-11-20에 원본에서 **관찰한 것**이에요. CSS 단계에서는 만들지 않아요.

- 슬라이드는 **10장**이고, 마지막 장 다음에 첫 장으로 이어져요. (Swiper `loop`: 원본 HTML에 `swiper-slide-duplicate`가 있어요)
- **자동으로 넘어가요.** 오른쪽 아래 일시정지(⏸) 버튼으로 멈출 수 있어요. (Swiper `autoplay`)
- 이전(<) · 다음(>) 버튼으로 넘겨요. (Swiper `navigation`)
- "2 / 10"처럼 **현재 장 / 전체 장**을 숫자로 보여 줘요. (Swiper `pagination`, `type: 'fraction'`)
- 가운데 카드 하나가 크게 보이고 양옆 카드가 걸쳐 보여요. 카드 사이 간격은 16px이에요. (Swiper `centeredSlides`, `slidesPerView: 'auto'`, `spaceBetween`)
- 자동 넘김 **시간(몇 초)**은 측정하지 않았어요. ⬜ JS 단계에서 측정

## 이 영역에서 배우는 CSS

| 개념 | 어디에 쓰나 | 📖 MDN |
| --- | --- | --- |
| position (복습) | 카드 = 기준 상자, 글자 묶음 = absolute | [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) |
| overflow | 둥근 모서리 밖으로 나가는 사진 자르기, 양옆 카드 자르기 | [overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow) |
| border-radius | 카드 모서리, 원형 버튼 | [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) |
| object-fit | 사진이 찌그러지지 않게 채우기 | [object-fit](https://developer.mozilla.org/ko/docs/Web/CSS/object-fit) |
| rgba 색 | 반투명 글자·테두리·버튼 배경 | [rgb()](https://developer.mozilla.org/ko/docs/Web/CSS/color_value/rgb) |
| flex (복습) | 카드 3장 가로 나열, 버튼 안 글자+아이콘 | [flexbox](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox) |

## 이미지

- 원본 슬라이드 사진은 프로젝트에 없어요. 지금은 `assets/images/hero_img_1_1.png`, `hero_img_1_2.png` 같은 **있는 이미지로 대신** 써요.
- 원본 사진이 꼭 필요하면 직접 내려받아 `assets/images/`에 넣으세요.
