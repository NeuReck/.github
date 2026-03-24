# NeuRack

AI 기반 강아지 품종 인식 및 커뮤니티 플랫폼을 개발하는 팀 조직입니다.

## 프로젝트 개요

강아지 사진을 업로드하면 AI가 품종을 식별하고, 해당 품종의 질병 정보 및 추천 정보를 제공합니다. 커뮤니티 기능을 통해 사용자 간 소통도 지원합니다.

## 레포지토리

### [dog-ai-agent_mvp](https://github.com/NeuRack/dog-ai-agent_mvp)

메인 MVP 애플리케이션. 프론트엔드, 백엔드, AI 서비스가 모노레포로 구성되어 있습니다.

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

### [dog-classifier-models](https://github.com/NeuReck/dog-classifier-models)

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
- Phase 3: 추가 최적화

```
dog-classifier-models/
├── backbone_comparison.ipynb   # 메인 실험 노트북
├── requirements.txt
└── experiments/                # 학습 결과 (CSV, PNG)
```

## 기술 스택 요약

| 분야    | 기술                                                          |
| ------- | ------------------------------------------------------------- |
| Mobile  | React Native, Expo, TypeScript, NativeWind                    |
| Backend | FastAPI, Python 3.11, Supabase                                |
| AI/ML   | TensorFlow, MobileNetV2, EfficientNetB0, GradCAM, GPT-4o-mini |
| Infra   | Vercel, GitHub Actions, ngrok                                 |
