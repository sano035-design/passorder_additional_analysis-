# Output 폴더 안내

본 `output/` 디렉토리는 데이터 분석 스크립트 실행 결과로 생성되는 **모든 데이터 분석 결과 및 최종 산출물(대시보드.html 등)**이 저장되는 폴더입니다.

---

## 1. 보관 대상 산출물
* **한국어 대시보드**:
  - [`passorder1_dashboard.html`](passorder1_dashboard.html): 한국어 버전 독립 실행형 HTML 대시보드
* **영문 대시보드 (English Dashboard)**:
  - [`passorder1_dashboard_en.html`](passorder1_dashboard_en.html): 영문 버전 독립 실행형 HTML 대시보드 (루트)
  - [`en/passorder1_dashboard.html`](en/passorder1_dashboard.html): 영문 버전 대시보드 (`output/en/` 서브디렉토리)
  - [`en/index.html`](en/index.html): GitHub Pages 및 정적 웹 호스팅용 영문 메인 엔트리

## 2. 산출물 관리 원칙
1. **다국어 지원 및 상호 전환**: 국문과 영문 대시보드 우측 상단에 상호 전환 버튼(`🌐 English Dashboard` / `🌐 한국어 대시보드`)이 탑재되어 브라우저에서 즉시 교차 탐색 가능합니다.
2. **독립 실행성 보장**: 모든 HTML 대시보드는 외부 웹 서버 없이 로컬 파일 시스템에서 브라우저로 열었을 때 차트와 인터랙션이 정상 작동합니다.
3. **GitHub Pages 배포**: `output/en/index.html`을 활용해 GitHub Pages 영문 포트폴리오 사이트로 즉시 서비스 가능합니다.
