# 2부 학습 계획: 같은 클론코딩으로 배우는 JavaScript

> **언제?** 1부 CSS(`docs/study-plan.md`) 8단계를 마친 뒤 시작해요.
> **방식은 1부와 같아요:** 한 단계 = 화면에서 **움직이게 할 것 1개 + 새 JS 개념 1~2개**.
> 지금 만드는 HTML·CSS를 **버리지 않고 그대로 이어서** 움직이게 만들어요.

## 전체 지도

| 단계 | 움직이게 할 것 | 핵심 개념 | 쓰는 곳 |
| --- | --- | --- | --- |
| J0 | JS 연결, 콘솔 찍어 보기 | `<script defer>`, `console.log`, 변수, 자료형 | `js/main.js` |
| J1 | 언어 선택 목록 열고 닫기 | 요소 찾기(`querySelector`), 클릭 이벤트, `classList` | 헤더 유틸 |
| J2 | 하위 메뉴(depth2) 열고 닫기 | 여러 요소 다루기(`querySelectorAll`, 반복문), `aria-expanded` | 헤더 메뉴 |
| J3 | 히어로 슬라이드 | **Swiper 연결과 옵션** (1부에서 미뤄 둔 값들) | 히어로 |
| J4 | 다른 슬라이드 영역 | Swiper 옵션 재사용, 함수 만들기 | 코스·축제·이벤트 등 |
| J5 | 홍보 배너를 데이터로 그리기 | 배열·객체, `fetch`, JSON, 템플릿 문자열 | 홍보 배너 (`data/promo-banner.json`) |
| J6 | 모바일 메뉴, 맨 위로 버튼 | 스크롤·크기 이벤트, 조건문 | 전체 |
| J7 | 마무리 | 코드 정리, 접근성 점검(키보드만으로 사용해 보기) | 전체 |

---

## 지금(CSS 단계)부터 지켜 두면 JS가 쉬워지는 약속 ✅

이 약속은 `CLAUDE.md`에도 적혀 있어요.

1. **상태는 클래스로 표현해요.** 열림·선택 같은 상태는 `is-` 로 시작하는 클래스를 써요.
   - 예: `.language-layer.is-open { display: block; }`
   - CSS 단계에서는 `:hover`로 확인하고, JS 단계에서는 JS가 `is-open`을 붙였다 뗐다만 하면 돼요.
   - Swiper가 자동으로 붙이는 클래스(`swiper-slide-active`)는 Swiper 규칙을 따라요.
2. **`id`는 스타일에 쓰지 않아요.** `id`는 JS와 접근성(`aria-controls` 등)용으로 남겨 둬요. 스타일은 클래스로만 줘요.
3. **숨기는 방법을 한 가지로 통일해요.** 기본은 숨기고(`display: none`), 상태 클래스가 붙으면 보이게 해요.
4. **하드코딩을 줄여요.** 색·크기는 `css/tokens.css`의 변수를 써요. JS에서도 같은 값을 읽을 수 있어요.
5. **버튼은 `<button>`, 이동은 `<a>`.** 클릭해서 무언가를 여닫는 건 `<button>`이어야 키보드로도 쓸 수 있어요.

---

## 폴더 구조 (J0에서 만들어요)

```
css-basic/
├ clone-exercise.html
├ css/
│ ├ reset.css
│ ├ tokens.css
│ └ clone-exercise.css
├ js/
│ └ main.js          ← J0에서 새로 만들어요
└ data/
  └ promo-banner.json
```

## 미리 알아 둘 것

- **Swiper**는 CSS 파일과 JS 파일을 둘 다 연결해야 해요. 연결은 J3에서 해요.
- `data/promo-banner.json`에는 원본 사이트의 이미지 주소가 들어 있어요. `fetch`로 이 파일을 읽으려면 파일을 **직접 더블클릭해서 열면 안 되고**, VS Code의 **Live Server** 같은 로컬 서버로 열어야 해요.

📖 [MDN: JavaScript 안내서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide) · [MDN: querySelector](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector) · [MDN: classList](https://developer.mozilla.org/ko/docs/Web/API/Element/classList) · [MDN: fetch](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch) · [Swiper 공식 문서](https://swiperjs.com/get-started)
