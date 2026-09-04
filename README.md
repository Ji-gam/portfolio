# 이은호 — 구조생화학 × AI/데이터 포트폴리오

구조생화학(단백질 구조 규명) 석사 전공과 제약 QC 실무 경험 위에 AI·데이터 분석 역량을 더한 바이오 × AI 융합 인재입니다.
㈜유한화학에서 원료의약품(API) QC를 11개월 수행하며 GMP·데이터 신뢰성을 체득했고, 석사 과정에서 AKTA 정제~결정화·XRD·Cryo-EM 구조 분석까지 항원-항체 결합 구조 규명 연구를 수행했습니다. 이후 오즈코딩스쿨 [초격차] AI 헬스케어 4기 과정을 통해 Python/SQL·머신러닝·딥러닝(CV)·LLM/RAG·FastAPI 백엔드까지 이수했습니다.

📓 [상세 포트폴리오(Notion)](https://app.notion.com/p/3d1d3ba6af7c812c8056e8fa81f1c0e6?pvs=204) · 📧 surt2415@naver.com

---

## Highlights

- **DACON 난임 임신 성공 예측 해커톤** — 시술 유형별 '논리적 결측치' 처리로 ROC-AUC `0.536 → 0.7422`
- **ReMedi 복약관리 플랫폼** — 5인 팀 팀장 겸 인프라 담당, OCR·공공데이터 API·LLM 결합 서비스를 AWS EC2 자동 배포까지 구축 (개인 커밋 356건 / 팀 전체 52%)
- 비동기 아키텍처 실측: 동시성 100에서 P95 `678.8ms vs 30,475.7ms` (45배 차이), EC2 실배포 환경에서 SLA 충족까지 검증
- 실험실과 코드베이스에서 동일한 가설 → 실험 → 검증 → 기록 사이클을 반복 — 실패 원인까지 정량 분석해 다음 의사결정 근거로 기록

---

## Projects

### 💊 [ReMedi — 진료 기록 기반 복약 안내 시스템](https://github.com/Ji-gam/AH_04_02)
`AI 헬스케어 4기 파이널 프로젝트 · 2팀 · Uponati(어포나티) 참여기업 주제` `팀장 · 인프라/CI-CD 담당`

처방전 사진을 OCR로 인식해 약품을 식별하고, 복약 스케줄·DUR(병용금기)·음식-약물 상호작용 및 생활습관 개선 가이드까지 자동 생성하는 서비스.

- OCR(CLOVA)+정규식+LLM 다중경로 약품명 추출, 2.7만건 약품 마스터 DB 퍼지매칭
- 식약처 공공데이터 4종 API를 로컬DB → MySQL → 외부API 3-Tier 폴백 구조로 연동
- FastAPI 이벤트 루프 블로킹 문제를 async I/O 벤치마크로 실측·해결 (P95 45배 개선)
- GitHub Actions CI + EC2 자동 배포 파이프라인 전담 구축, 개인 커밋 356건(팀 전체 52%)

`Python` `FastAPI` `MySQL` `React` `Vite`

### 🫁 [흉부 X-ray AI 진단 웹 서비스 백엔드](https://github.com/Ji-gam/Mp_4_FastAPI)
`팀 프로젝트 · 2조 · 9일 단계별 미션`

직원이 환자·진료기록을 관리하고, 업로드한 흉부 X-ray를 AI로 분석해 폐렴 여부와 Grad-CAM 히트맵을 확인하는 서비스.

- FastAPI 내 AI 추론의 이벤트 루프 블로킹 문제를 식별해 Redis 기반 이벤트 아키텍처(EDA)로 전환
- Grad-CAM 직접 구현(순전파 점수 → 역전파 그라디언트 → 활성화맵 가중합)
- Docker Compose 4서비스(fastapi/mysql/redis/ai-worker) 구성, AWS EC2 배포

`FastAPI` `Redis` `PyTorch` `Docker Compose` `AWS EC2`

### 🐾 [GapFlag](https://github.com/Ji-gam/GapFlag)
`개인 프로젝트`

동물용 의약품 타깃·성분을 연구 공백(기회)과 위험 신호로 교차 검증하는 스크리닝 도구.

`Python` `FastAPI`

### 🤰 난임 환자 임신 성공 여부 예측
`DACON × 오즈코딩스쿨 해커톤 · 3조` `ROC-AUC 0.536 → 0.7422 (Public LB 0.7421764204)`

- 시술 유형별 논리적 결측치 처리, 도메인 기반 텍스트 파싱 피처 엔지니어링
- 신규 피처 12종 Ablation Study — 실패 피처의 원인까지 정량 분석
- IVF/DI 분리 모델링 + PyTorch 오토인코더 하이브리드
- Nelder-Mead 제약 스태킹으로 6종 베이스 모델 앙상블 가중치 직접 최적화

`pandas` `scikit-learn` `LightGBM/CatBoost/XGBoost` `Optuna` `PyTorch`
> 노트북 기반 해커톤 프로젝트로 별도 GitHub 저장소 없음 — 상세 내용은 [Notion 포트폴리오](https://app.notion.com/p/3d1d3ba6af7c812c8056e8fa81f1c0e6?pvs=204) 참고.

---

## Research — 바이오 (석사 과정, 건국대학교 화학과)

- **TROP2 항원-항체 결정화 조건 개선** — 발현 시스템을 HEK293 → E.coli로 전환하는 가설 검증, 결정 생성 확률 **6배 상승**, 생산비·기간 30% 단축
- **PD-1/Ivonescimab Fab 결합 실패 원인 규명** — Glycosylation이 결합의 가교라는 가설을 조건별 분리 실험으로 검증
- **Datopotamab-TROP2 결합 구조 규명** (2025 FDA 승인 ADC 항체) — X선 결정법으로 에피토프 규명, cis/trans 이중체 형성 구조적 영향 해석
- **ANGPTL3-Evinacumab 결합 실패 원인 규명** — 서열 비교로 종/이소형 불일치라는 근본 원인 규명
- **AlphaFold2 도입** — CDR 구조 규명 시간을 수작업 대비 4~6시간 단축, 연구실 표준 절차로 채택

상세 내용(전 실험 설계·가설·검증 과정)은 [Notion 포트폴리오](https://app.notion.com/p/3d1d3ba6af7c812c8056e8fa81f1c0e6?pvs=204) 참고.

---

## Skills

| 분야 | 기술 |
|---|---|
| 바이오 | AKTA 정제, SEC, 단백질 결정화, XRD, Cryo-EM, PyMOL/CCP4/Coot, AlphaFold2, HEK293/E.coli 발현, QC/GMP |
| Data/ML | Python, SQL, Pandas/NumPy, scikit-learn, XGBoost/LightGBM/CatBoost, Optuna, PyTorch, CV(YOLOv8·Grad-CAM), LLM/RAG(LangChain·Chroma·BM25+RRF·Reranker) |
| Backend/Infra | FastAPI(async), SQLAlchemy/Alembic, MySQL, Redis, Docker, AWS EC2, Nginx, GitHub Actions CI/CD, TypeScript/React |

## Education

- 건국대학교(서울) 대학원 화학과 석사 · 구조생화학 — 2024.03 ~ 2026.02, 학점 4.5/4.5
- 건국대학교(서울) 화학과 학사 — 2016.03 ~ 2023.02, 학점 3.71/4.5
- 오즈코딩스쿨 [초격차] AI 헬스케어 4기 — 2026.02 ~ 2026.08

## Experience

- ㈜유한화학 — QC(API) / 사원, 2022.11 ~ 2023.09 (11개월)

## Certifications

데이터분석 준전문가(ADsP) · OPIc Intermediate Mid 1급 · JLPT N1
