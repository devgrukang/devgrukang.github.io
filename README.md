# devgrukang.github.io

강은성(Eunsung Kang)의 웹 이력서 — GitHub Pages.

- `index.html` — 국문/영문 전환 반응형 이력서 (정적, 의존성 없음). 직무 탭 `?role=quality|site|ops`, 쇼릴 자동 흐름·드래그·터치.
- `print/ko.html`, `print/en.html` — 한 권 PDF의 원본 (1부 이력서 → 2부 자기소개서).
- `print/promo-sheet.html`, `print/promo-sheet-en.html` — 3부 홍보 시트 (A4 1쪽, QR·벽화·4지표·3컷·근무 조건).
- `files/` — 공개용 PDF. 통합본 `Eunsung_Kang_Resume_2026_KO.pdf`(4쪽) / `_EN.pdf`(4쪽) — 1·2부 3쪽 + 3부 1쪽, 3부 단독 `Eunsung_Kang_Promo_Sheet_2026.pdf` / `_EN.pdf`.
- 빌드 단계 없음. PDF는 라이브 인쇄 화면을 A4로 인쇄해 만들고, 마지막에 3부 시트를 합친다.
- 상세 주소·생년월일·급여는 넣지 않는다. 웹 공개본에는 친필서명을 넣지 않는다(2026-11-24 제거, 서명 자리에는 보안상 제외 안내만 둔다).

## PDF 다시 뽑기 (2026-11-24)

```
python3 tmp/build_site.py --proof-dir career/site-print-<날짜>/proof   # 4종 + 150dpi 렌더
python3 scripts/docqa.py check files/*.pdf --profile resume --passes 3 --report-dir reports/docqa
```

- `print/fonts/`는 `career/direct-apply/assets/make_fonts.py`가 만든 정적 서브셋을 복사해 둔 것. 구글 가변폰트를 쓰면 크로미움이 글자를 **Type3(그림)** 으로 떨어뜨려 글꼴이 임베드되지 않는다. 인쇄 HTML은 반드시 이 로컬 `@font-face`를 쓴다.
- 홍보 시트 단독 PDF 2종도 같은 스크립트가 만든다.
