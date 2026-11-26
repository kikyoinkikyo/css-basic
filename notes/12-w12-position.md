# 12. W12 position — 개념 정리

> 연습한 곳: 대한민국 구석구석 메인 **AI 기사 요약 카드**, **머리글** (2026-11-26)
> W12-3(AI 슬라이드 이전·다음 버튼)은 진행 중이에요.

| 개념 | 한 줄 뜻 | 예시 코드 | 자주 하는 실수 |
|---|---|---|---|
| `static` | position 기본값이에요. `top`·`left` 등이 먹지 않아요. | (따로 안 씀) | `top`을 줬는데 왜 안 움직이는지 헷갈려요. |
| `relative` + `absolute` 짝꿍 | 부모에 `relative`, 얹을 것에 `absolute`를 주면 부모를 기준으로 배치돼요. | `.card { position: relative; } .badge { position: absolute; top: 8px; right: 8px; }` | 부모에 `relative`가 없어서 엉뚱한 조상(또는 첫 화면)을 기준으로 배치돼요. |
| 문서 흐름에서 제외 | `absolute`·`fixed` 요소는 자리를 차지하지 않아요. 다른 요소를 밀어내지 않아요. | — | 뒤에 오는 내용이 그 아래로 겹쳐 들어가는 걸 예상 못 해요. |
| `bottom` | 기준 상자의 **아래에서** 얼마나 떨어진 곳에 놓을지예요. | `bottom: 36px;` | 위에서 계산해 `top`으로 맞춰서, 상자 높이가 바뀌면 자리가 틀어져요. |
| 음수 위치 | 기준 상자 **바깥**으로 나가게 배치해요. | `left: -19px;` | — |
| `fixed` | **화면(뷰포트)** 기준으로 항상 그 자리에 있어요. 흐름에서 제외돼요. | `.header { position: fixed; top: 0; left: 0; right: 0; }` | 자리를 차지하지 않아서 첫 화면 내용이 헤더에 가려져요 → 본문에 위 여백을 줘요. |
| `sticky` | 스크롤하다 `top` 값에 닿으면 붙어요. 원래 자리는 남아요. | `.bar { position: sticky; top: 0; }` | `top`을 안 써서 붙지 않아요. |
| `z-index` | 겹칠 때 숫자가 큰 쪽이 위에 와요. position이 지정된 요소에서 먹어요. | `z-index: var(--z-header);` | `static` 요소에 줘서 아무 변화가 없어요. |
| 마진 상쇄 | 위아래 바깥 여백이 맞닿으면 더해지지 않고 **큰 값 하나만** 남아요. | 부모 `margin-top: 90px` + 첫 자식 `162px` → **162px** | 252px가 될 거라고 생각해요. 부모에 안쪽 여백·테두리가 있으면 상쇄되지 않아요. |
| `box-sizing` | `border-box`는 `height`에 안쪽 여백·테두리가 포함되고, `content-box`는 글자 칸만이에요. | `box-sizing: content-box;` | `border-box`인데 글자 칸 높이를 그대로 써서 마지막 줄이 잘려요. |

## 내 코드에서 찾기
- 머리글 고정: `css/style.css:63` (`.header` `position: fixed`), `:69` (`z-index: var(--z-header)`)
- 히어로 위 여백(마진 상쇄): `css/style.css:177` (`.hero-sec` `margin: 162px auto 0`)
- 하위 메뉴 레이어: `css/style.css:128` (`.depth2-wrap` `position: absolute`)
- 언어 선택 레이어: `css/style.css:162` (`.language-layer` `position: absolute`)
- AI 카드 기준 상자: `css/style.css:428` (`.sw-ai .swiper-slide .cont` `position: relative`)
- 이름표·사진: `css/style.css:437`, `:497` (`absolute`, `top` 기준)
- 바로가기 `bottom` 배치: `css/style.css:511`, `:513` (`bottom: 36px`)
- 요약글 글자 칸 높이: `css/style.css:483` (`box-sizing: content-box`), `:491` (`-webkit-line-clamp: 6`)
- 토큰: `css/tokens.css` `--z-header: 110`, `--header-height: 90px`

## 이번에 받은 피드백
- 본문 여백은 **마진 상쇄**를 확인해서 원본 값을 정해요(원본 90px + 162px → 162px).
- `border-box`에서는 `height`에 안쪽 여백·테두리가 포함돼요. 원본과 다르면 그 요소만 `content-box`로 바꿔요.
- 세로 가운데는 `line-height` 대신 원본처럼 flex + `align-items`로 맞춰요.
- 굵어 보이는 차이는 값(700 → 500)으로 맞추지 말고 원인(글꼴 파일)을 찾아요. ⏸️ 바로가기 굵기는 글꼴 연결 정리 때.
- 높이·z-index처럼 여러 곳에서 쓰거나 순서를 모아 볼 값은 토큰으로 써요.

## 공식 문서
- [position (MDN)](https://developer.mozilla.org/ko/docs/Web/CSS/position)
- [포함 블록 (MDN)](https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block)
- [z-index (MDN)](https://developer.mozilla.org/ko/docs/Web/CSS/z-index)
- [마진 상쇄 (MDN)](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_box_model/Mastering_margin_collapsing)
- [box-sizing (MDN)](https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing)

## 내 말로 한 줄 요약
- (직접 써 보세요)
