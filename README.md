<div align="center">

# 🧭 CAMPASS

**서경대학교 캠퍼스 길찾기 서비스**

말로 묻고, 사진으로 위치를 찾고, 헤매기 쉬운 곳은 미리 알려 주는 캠퍼스 내비게이션

[![서비스 바로가기](https://img.shields.io/badge/서비스_바로가기-2563EB?style=for-the-badge&logo=vercel&logoColor=white)](https://swce2026-team13.vercel.app)
[![관리자 페이지](https://img.shields.io/badge/관리자_페이지-334155?style=for-the-badge&logo=googleanalytics&logoColor=white)](https://swce2026-team13.vercel.app/admin)

![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch_DINOv2-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)

</div>

---

## 🔗 바로가기

| 구분 | 링크 |
|---|---|
| 일반 사용자 | https://swce2026-team13.vercel.app |
| 관리자 | https://swce2026-team13.vercel.app/admin (계정은 팀에 문의) |

## 💡 왜 만들었나요?

언덕 위에 건물이 붙어 있는 서경대학교는 **건물 사이를 층과 연결통로로 오가야 해서** 처음 온 사람이 길을 잃기 쉽습니다.
CAMPASS는 지금 겪는 불편을 바로 해결하고, 그 과정에서 모인 기록으로 **헤매기 쉬운 구간을 찾아 미리 대응**하도록 돕습니다.

## ✨ 주요 기능

### 🗣️ 자연어 목적지 검색
- "면접 보러 왔어요", "엘리베이터로 가고 싶어요"처럼 말하듯 물어보면 목적지와 이동 조건을 파악합니다.
- 규칙 기반 분석을 먼저 쓰고, 모호한 질문만 Gemini로 보완합니다(응답 제한 3초, 실패 시 규칙 검색으로 전환).
- 30분 동안 대화 맥락을 기억해 "그럼 계단으로는?" 같은 후속 질문도 이해합니다.

### 📷 사진으로 현재 위치 찾기
- DINOv2로 사진의 특징을 뽑아 기준 사진 301장과 비교하고, 비슷한 지점 후보를 최대 3개 보여 줍니다.
- 위치를 다시 확인한 기록은 혼란 구간을 찾는 데 쓰입니다.
- **테스트 결과:** 사진 24장 중 1순위 정답 87.5%, 상위 3개 안 정답 91.7%

### 🗺️ 지도·경로 안내
- 2D·3D 지도에서 장소를 고르면 건물·층·연결통로 그래프에서 다익스트라로 경로를 찾습니다.
- 계단·엘리베이터 조건을 반영해 단계별로 안내하고, 위치를 다시 고르면 그 지점부터 다시 계산합니다.

### ⚠️ 혼란 구간 안내
- 위치 재확인과 도착 후 제보를 지점별로 집계해 혼란 비율과 원인을 계산합니다.
- 헤맨 기록이 있는 지점은 안내 중에 미리 주의 사항을 보여 줍니다.

### 📊 관리자 인사이트
- 기간·건물·원인별 통계, 혼란 지점 우선순위 표, 헤맨 지점 지도를 한 화면에서 봅니다.
- 반복해서 헤맨 취약 구간을 찾아 표지판 보강이나 인력 배치 순서를 정할 수 있습니다.

## 🏗️ 구조

```
campass/          Next.js 웹 앱 (화면, API, 경로 계산, 관리자 통계)
vision-server/    사진 위치 인식 서버 (FastAPI + DINOv2)
docs/             프로젝트 문서
```

## 🚀 로컬에서 실행하기

Node.js 24.x가 필요합니다. 저장소 최상위 폴더에서 실행합니다.

```bash
npm --prefix campass ci
npm run dev
```

브라우저에서 http://localhost:3000 을 엽니다.
환경 변수와 자세한 실행 방법은 [campass/README.md](campass/README.md)를 참고하세요.

## 👥 팀

서경대학교 2026 소프트웨어공학 13팀 (swce2026-team13)
