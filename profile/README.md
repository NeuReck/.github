# NeuRack

AI 기반 서비스를 기획하고 개발하는 팀입니다.

## 프로젝트

### [댕슐랭 — dog-ai-agent_mvp](https://github.com/NeuRack4/dog-ai-agent_mvp)

반려견 사진 한 장으로 견종을 분석하고, 유전 질환 기반 맞춤 영양소·식재료·레시피를 추천하는 AI 서비스입니다.

| 영역           | 기술 스택                                       | 설명                                               |
| -------------- | ----------------------------------------------- | -------------------------------------------------- |
| **Frontend**   | React Native (Expo ~52), TypeScript, NativeWind | 모바일 앱 — 로그인, 품종 감지, 질병 정보, 커뮤니티 |
| **Backend**    | FastAPI (Python 3.11), Supabase PostgreSQL, JWT | 인증, AI 추론, 사용자 데이터 API                   |
| **AI Service** | TensorFlow MobileNetV2, GradCAM                 | 품종 인식 모델 서빙 (port 8001)                    |
| **API Proxy**  | Vercel Edge Functions                           | 프론트엔드 → 백엔드 프록시                         |
| **Infra**      | Vercel, ngrok (dev), GitHub Actions CI/CD       | 배포 및 자동화                                     |

**주요 엔드포인트:** `/ai/breed-recognition`, `/ai/gradcam`, `/breeds`, `/community/posts`

```
dog-ai-agent_mvp/
├── frontend/        # React Native (Expo) 모바일 앱
│   └── src/
├── backend/         # FastAPI 서버
│   ├── routers/     # API 라우트
│   ├── services/    # 비즈니스 로직
│   ├── models/      # 데이터 모델
│   └── migrations/  # DB 마이그레이션
├── ai-service/      # AI 모델 서버
│   ├── breed/       # 품종 인식
│   ├── dog-detection/ # 강아지 탐지
│   ├── LLM/         # LLM 연동
│   └── gen-img/     # 이미지 생성
├── api/             # Vercel Edge Functions
└── data/            # 데이터 파일
```

---

### [dog-classifier-models](https://github.com/NeuRack4/dog-classifier-models)

Stanford Dogs 데이터셋 기반 120개 품종 분류 모델 실험 레포입니다.

| 항목          | 내용                                                  |
| ------------- | ----------------------------------------------------- |
| **목적**      | 백본 아키텍처 비교 및 최적 모델 선정                  |
| **환경**      | TensorFlow 2.16.2, Apple M2 Mac                       |
| **비교 모델** | MobileNetV2, MobileNetV3Large, EfficientNetB0         |
| **최종 선택** | **EfficientNetB0** — Val Acc 85.52%, Top-5 Acc 98.67% |

**학습 단계:**

- Phase 1: 백본 비교 (MobileNetV2 77.9% → EfficientNetB0 85.5%)
- Phase 2: Early Stopping 적용 → 86.9%
- Phase 3: 추가 학습 시도 → 유의미한 개선 없음, Phase 2 채택

```
dog-classifier-models/
├── backbone_comparison.ipynb   # 메인 실험 노트북
├── requirements.txt
└── experiments/                # 학습 결과 (CSV, PNG)
```

---

### [Spring-of-Marketing](https://github.com/NeuRack4/Spring-of-Marketing)

제품 정보와 목표를 입력하면 AI가 콘텐츠를 생성 → 검증 → 배포 → 개선하는 풀사이클 마케팅 자동화 에이전트입니다.

| 영역            | 기술 스택                        | 설명                            |
| --------------- | -------------------------------- | ------------------------------- |
| **Frontend**    | Next.js, Vercel                  | 웹 클라이언트                   |
| **Backend**     | FastAPI, Supabase                | API 게이트웨이, 데이터 관리     |
| **AI Services** | OpenAI API, Claude API, ChromaDB | 콘텐츠 생성, 페르소나 검증, SEO |
| **Infra**       | AWS EC2, Docker, GitHub Actions  | 배포 및 CI/CD                   |

**주요 서비스:** AI 콘텐츠 생성, 페르소나 시뮬레이션, SEO/GEO 최적화, 성과 데이터 수집

```
spring-of-marketer/
├── frontend/          # Next.js 웹 클라이언트 (Vercel 배포)
├── backend/           # FastAPI 메인 API 게이트웨이 (Supabase 연동)
├── ai-content/        # AI 콘텐츠 생성 서비스 (OpenAI, Claude API)
├── ai-persona/        # AI 페르소나 검증/시뮬레이션 서비스 (ChromaDB)
├── ai-seo/            # SEO/GEO 최적화 서비스
├── data-collector/    # 성과 데이터 수집 서비스
├── infra/             # Docker, CI/CD, AWS 인프라 설정
└── docs/              # 프로젝트 문서
```

---

## 기술 스택 요약

| 분야    | 기술                                                                  |
| ------- | --------------------------------------------------------------------- |
| Mobile  | React Native, Expo, TypeScript, NativeWind                            |
| Web     | Next.js, Vercel                                                       |
| Backend | FastAPI, Python 3.11, Supabase, JWT                                   |
| AI/ML   | TensorFlow, MobileNetV2, EfficientNetB0, GradCAM, GPT-4o-mini, Claude |
| Data    | ChromaDB, PostgreSQL                                                  |
| Infra   | Vercel, AWS EC2, Docker, GitHub Actions, ngrok                        |
