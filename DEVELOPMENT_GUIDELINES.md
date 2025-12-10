# DDS Development Guidelines

## 기본 원칙

- Figma Code Connect 매핑 우선. 매핑 불가 시 최소 커스텀 구현으로 작업
- Figma 디자인과 **시각적으로** 정확하게 일치하는 형태로 구성한다. 임의 추측하지 않는다

---

## 금지 사항

- 추측 애니메이션/상호작용 금지
- 기능 과추측 / 디자인 미존재 요소 임의 추가 금지
- 임의로 추측한 여백(margin/padding) 확장 금지
- 패턴 중복 구현 금지
- 의미 없는 임의 요소/문구 추가 금지
- DDS 디자인 토큰 추론 금지

---

## 작업 순서 권장 플로우

1. 디자인 토큰 SCSS 확인 (`scss/abstracts/_variables.scss`)
2. Figma 링크 내 Code Connect 매핑 가능한 컴포넌트 식별
3. Figma 수치에 맞게 크기 및 여백 조정
4. SVG 코드 반영 시 Figma 디자인과 불일치하면 다운로드하여 반영
5. 반복 패턴 단위 컴포넌트 작성 (반복 패턴 우선)
6. 시각적으로 Figma와 정확히 일치하는지 최종 확인
7. ESLint + Prettier 검사 통과
8. 컴포넌트 작성 시 기능/단위 테스트 진행 및 통과
9. HTML/CSS/JS 단위테스트 기능테스트 통과
