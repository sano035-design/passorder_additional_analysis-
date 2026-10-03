# 대시보드 및 웹페이지 디자인 시스템 표준 명세서 (design.md)

본 문서는 신규 프로젝트에서 데이터 분석 대시보드 및 웹페이지를 제작할 때 준수해야 하는 **UI/UX 디자인 시스템 표준 가이드라인(Design Tokens & Component Specifications)**입니다.

사용자에게 높은 신뢰감과 시각적 몰입감(Visual Impact)을 선사하기 위해 검증된 **프리미엄 다크 테마(Full Dark Aesthetic)**를 기본으로 채택하며, 브랜드 아이덴티티에 따라 액센트 컬러를 커스터마이징할 수 있도록 설계되었습니다.

---

## 1. 디자인 컨셉 및 원칙 (Core Principles)

1. **High-End Dark Aesthetic (몰입형 다크 테마)**:
   - 깊이 있는 다크 블랙(`--bg-root: #0A0C10`)을 캔버스로 삼아 데이터 시각화의 명도 대비를 극대화하고 장시간 분석 시 눈의 피로를 최소화합니다.
2. **Signature Accent & Layered Cards (입체적 카드 레이어)**:
   - 최상위 배경 위에 서피스 카드(`--bg-card: #181B26`)와 미세 보더(`--border-dark: #262A3B`)를 둘러 컴포넌트 간의 뚜렷한 시각 위계(Visual Hierarchy)를 확립합니다.
   - 프로젝트 고유의 시그니처 색상(예: 오렌지, 바이올렛, 에메랄드 등)으로 핵심 KPI와 활성 탭에 생동감을 부여합니다.
3. **Clutter-Free Data Table (정돈된 노-랩 표 레이아웃)**:
   - 표 내부의 텍스트가 줄바꿈되어 깨지는 현상을 방지하기 위해 모든 데이터 셀에 `white-space: nowrap`을 강제합니다.
4. **Direct Value Labels (차트 수치 상시 표기)**:
   - 막대 차트의 경우 마우스 호버에만 의존하지 않고, 막대 최상단에 실제 수치(예: `85.4%`, `+12.8%`)가 흰색 볼드로 상시 노출되도록 구현합니다.

---

## 2. 디자인 토큰 명세 (CSS Variables)

신규 프로젝트 생성 시 `:root`의 **브랜드 액센트 컬러**를 해당 서비스의 대표 컬러로 지정하여 활용합니다:

```css
:root {
  /* 1. 브랜드 액센트 컬러 (프로젝트 브랜드에 맞게 Hex 수정) */
  --brand-primary: #FF5C1E;                           /* 메인 브랜드 컬러 (예: 오렌지, 퍼플 등) */
  --brand-hover: #E84D12;                             /* 버튼 및 호버 인터랙션 */
  --brand-gradient: linear-gradient(135deg, #FF6525 0%, #FF4500 100%); /* KPI 카드 메인 그라데이션 */
  --brand-glow: rgba(255, 92, 30, 0.25);             /* 포커스 및 네온 효과 */

  /* 2. 서피스 및 배경 (Dark Surface System) */
  --bg-root: #0A0C10;                                 /* 최상위 페이지 캔버스 배경 (Deep Dark) */
  --bg-header: #12141C;                              /* 상단 헤더 및 탭 네비게이션 서피스 */
  --bg-card: #181B26;                                /* 메인 차트 및 패널 카드 서피스 */
  --bg-card-hover: #1E2230;                          /* 인터랙티브 카드 호버 서피스 */
  --bg-badge: rgba(255, 255, 255, 0.06);             /* 보조 배지 배경 */

  /* 3. 보더 및 구분선 */
  --border-dark: #262A3B;                            /* 표준 카드 및 컴포넌트 경계선 */
  --border-subtle: #1F2230;                          /* 테이블 행 및 얇은 디바이더 */

  /* 4. 타이포그래피 컬러 (고대비 스케일) */
  --text-pure-white: #FFFFFF;                        /* 순백색 (핵심 수치, 메인 헤더 타이틀) */
  --text-main: #E2E8F0;                              /* 본문 텍스트 및 카드 서브헤더 */
  --text-muted: #94A3B8;                             /* 축 라벨, 범례, 비활성 텍스트 */
  --text-dim: #64748B;                               /* 부가 캡션 및 미세 안내 문구 */

  /* 5. 시맨틱 성과 컬러 (Status & Lift) */
  --semantic-emerald: #10B981;                       /* 긍정 성과 / 대조군 대비 Lift (Green) */
  --semantic-emerald-soft: rgba(16, 185, 129, 0.15); /* 에메랄드 소프트 배지 배경 */
  --semantic-rose: #F43F5E;                          /* 하락 / 경고 / 이탈 (Red) */
  --semantic-rose-soft: rgba(244, 63, 94, 0.15);     /* 로즈 소프트 배지 배경 */

  /* 6. 형태 및 그림자 */
  --radius-xl: 18px;                                 /* 헤더 및 메인 패널 모서리 라운딩 */
  --radius-lg: 14px;                                 /* KPI 카드 및 내부 박스 라운딩 */
  --radius-md: 10px;                                 /* 탭 버튼 및 알약 배지 라운딩 */
  --radius-sm: 6px;                                  /* 차트 바 모서리 및 작은 태그 라운딩 */
  --shadow-dark: 0 10px 25px -5px rgba(0, 0, 0, 0.5), 0 8px 10px -6px rgba(0, 0, 0, 0.3);
}
```

---

## 3. 타이포그래피 시스템 (Typography)

* **폰트 패밀리**:
  - 본문 및 한글 UI: `"Pretendard", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
  - 숫자 및 영문 KPI: `'Outfit', sans-serif` (모던 지오메트릭 폰트, 가독성과 심미성 극대화)
* **타이포그래피 위계 (Hierarchy)**:
  - `Header Title`: 22px, Weight 800, Letter-spacing -0.4px
  - `Panel / Section Title`: 18px, Weight 800, Letter-spacing -0.3px
  - `KPI Big Number`: 28px ~ 32px, Weight 900, Font Outfit
  - `Body / Cell Text`: 13px, Weight 500 / 700 (Data values)
  - `Badge / Tag Label`: 11px ~ 12px, Weight 700

---

## 4. 데이터 시각화 표준 규칙 (Chart.js Rules)

대시보드 내 차트 구현 시 준수해야 할 필수 설정:

1. **차트 공통 다크 스타일**:
   - 캔버스 배경 그리드: `borderColor: '#1E2230'`, `color: '#1E2230'`
   - 축 눈금 폰트: `family: "'Outfit', 'Pretendard'", size: 11, color: '#94A3B8'`
   - 라인 차트 텐션: `tension: 0.25` (자연스러운 곡선 처리)
   - 막대 모서리: `borderRadius: 6`
2. **막대 상단 수치 표기 플러그인 (Chart.js Data Labels)**:
   - 플러그인을 활용하여 막대 끝부분에 값을 직관적으로 렌더링:
     ```javascript
     plugins: [ChartDataLabels],
     options: {
       plugins: {
         datalabels: {
           anchor: 'end',
           align: 'top',
           color: '#FFFFFF',
           font: { family: 'Outfit', weight: 'bold', size: 12 },
           formatter: (value) => value + '%'
         }
       }
     }
     ```

---

## 5. 핵심 UI 컴포넌트 규격

### 5.1. 상단 공식 로고 컴포넌트
```css
.project-logo-badge {
  display: inline-flex;
  align-items: center;
  font-weight: 900;
  font-size: 26px;
  letter-spacing: -0.8px;
  padding: 6px 16px;
  background: #0E1017;
  border-radius: var(--radius-md);
  border: 1px solid var(--border-dark);
}
.logo-prefix { color: var(--text-pure-white); }
.logo-accent { color: var(--brand-primary); }
```

### 5.2. 대조군 A vs 실험군 B 식별 미니 카드
```css
.group-mini-card {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 8px 14px;
  border-radius: var(--radius-md);
  background: var(--bg-card);
  border: 1px solid var(--border-dark);
  font-size: 13px;
  font-weight: 600;
}
.group-mini-card.treatment {
  border-color: rgba(255, 92, 30, 0.4);
  background: rgba(255, 92, 30, 0.08);
}
```

### 5.3. 5대 핵심 KPI 그라데이션 카드
```css
.kpi-card {
  background: var(--brand-gradient);
  border-radius: var(--radius-lg);
  padding: 20px;
  color: var(--text-pure-white);
  box-shadow: var(--shadow-dark);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.kpi-title { font-size: 13px; font-weight: 700; opacity: 0.9; }
.kpi-value { font-family: 'Outfit', sans-serif; font-size: 30px; font-weight: 900; }
.lift-pill {
  display: inline-flex;
  padding: 4px 8px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.2);
  font-size: 11px;
  font-weight: 800;
  backdrop-filter: blur(4px);
}
```

### 5.4. No-Wrap 데이터 테이블
```css
.data-table {
  width: 100%;
  border-collapse: collapse;
}
.data-table th, .data-table td {
  padding: 12px 16px;
  border-bottom: 1px solid var(--border-subtle);
  white-space: nowrap; /* 글자 줄바꿈 원천 차단 */
  font-size: 13px;
}
.data-table th {
  background: #12141C;
  color: var(--text-muted);
  font-weight: 700;
  text-align: left;
}
```

---

## 6. 대시보드 품질 검증 체크리스트 (Quality Checklist)
- [ ] 데스크톱 1920x1080 및 1440x900 해상도에서 레이아웃 어긋남 없음
- [ ] 브라우저 콘솔 에러 0건 (F12 콘솔 창 확인)
- [ ] 모든 데이터 테이블 셀의 `white-space: nowrap` 적용 및 가로 깨짐 없음
- [ ] 막대 차트 상단에 흰색 볼드 수치 라벨 정상 출력
- [ ] 탭 전환 시 차트가 부드럽게 리사이징되며 겹침 현상 없음
