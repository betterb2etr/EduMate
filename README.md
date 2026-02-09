**original link: https://github.com/OpenSoftware-agentAI/AIagent_OS**
# EduMate
<img width="900" height="850" alt="image" src="https://github.com/user-attachments/assets/3906d91e-9f14-4986-b230-3f5764c9206f" />

## 🧭 Overview

> **EduMate**는 **AI 채팅 어플리케이션 서비스**로,  
> 자연어 대화만으로 학원 데스크의 반복적인 행정 업무를 자동화합니다.  
> 복잡한 설정이나 별도의 학습 과정 없이 **직관적인 웹 인터페이스**를 통해 누구나 쉽게 사용할 수 있으며,  
> AI가 빠르고 정확하게 처리하여 **업무 효율성을 극대화**합니다.

---

## 📈 Project Status

> **Status:** 🚀 **Operational (Live Service Running)**

EduMate는 현재 **실제 학원 환경에서 사용했으며**,  
AI 기반 대화형 시스템을 통해 **데스크 업무 자동화 및 피드백 생성** 을 중심으로 다양한 기능을 제공합니다.  
주요 기능은 안정적으로 동작하고 있으며, 사용자 피드백을 기반으로 **지속적인 기능 추가 및 리팩토링 작업**이 진행되고 있습니다.

실사례를 참고하여 일부 기능들이 작성되었습니다. 
학원의 저작권 보호를 위하여 학원 업무와 관련된 코드 및 문서들은 비공개 처리 및 주석처리되었습니다. 
비공개 처리된 파일의 자세한 위치는 BE/gitignore을 참고해주세요 

---

### ✅ 주요 기능

1. **엑셀 파일 업로드**

   - 학원 담당자가 학생 답안 및 점수 데이터를 엑셀 파일로 업로드
   - 문제별/학생별 데이터를 자동 파싱 및 저장
   - 데이터 저장 후 데이터 조회 가능 (ex : 전체 학생 데이터 조회) 

2. **문제별 코멘트 생성**
   
   <img width="300" height="200" alt="image" src="https://github.com/user-attachments/assets/3e16b7b3-8e26-449d-97fa-6b05e0a89a87" />


   - 데스크 선생님이 문제의 특징을 간단히 입력하면 **EduMate AI**가 각 문제에 대한 피드백을 자동 생성
   - 문제별 상황에 따른 코멘트 예시:
     ```text
     - 정답일 때: "이 유형은 정확하게 이해했네요! 계산도 빠릅니다. "
     - 오답일 때: "분모 통일 과정에서 실수가 있었어요. 개념 복습이 필요해요."
     - 보완점: "유사 문제를 2~3개 더 풀어보면 완벽하게 익힐 수 있습니다."
     ```

4. **학생별 코멘트 생성**

   - 문제별 코멘트를 종합하여 **학생 맞춤형 피드백 자동 생성**
   - 여러 문제를 틀린 학생 → **격려 중심 피드백**
   - 일부 실수한 학생 → **보완 중심 피드백**
   - 매번 다양한 문체로 자연스러운 코멘트 제공
   - 생성된 코멘트는 화면에서 즉시 확인 가능

5. **학부모용 데일리 테스트 이미지 생성**
   
     <img width="228" height="186" alt="에듀메이트 이미지 생성" src="https://github.com/user-attachments/assets/f7ff125c-03b1-4ee2-9d3c-f638169074b6" />

   - 학생별 점수, 코멘트가 포함된 **자동 이미지 생성**

7. **SMS 발송 기능**
   - 학부모님께 데일리 테스트 결과 이미지를 **문자(SMS)** 로 자동 송부
   - 발송 내역 및 상태를 시스템에서 확인 가능


---

##  🔑 기여

#### 사용자 파일 업로드 편의성 강화

- 학원 실무 상황을 반영, 사용자(원장 및 교사)가 직접 CSV 및 이미지 파일을 업로드할 수 있도록 프론트·백엔드 설계
- React 컴포넌트를 활용한 직관적인 파일 선택 및 업로드 진행 상태 알림
- 백엔드는 Multer 등 라이브러리로 안전하게 파일 처리하고, 업로드된 CSV 데이터를 자동으로 데이터베이스에 저장해 AI 분석에 활용

#### SMS 문자전송 서비스 연동

- SMS SDK를 통합하여 학부모 대상 맞춤형 문자 및 MMS 자동 발송 기능 구축
- 문자 성공 여부 및 에러에 대한 체계적 로깅과 예외 처리로 운영 안정성 확보
- AI 코멘트 및 이미지 생성 완료 후 자동 문자 발송 연동으로 완전한 업무 프로세스 자동화 실현

#### 실시간 진행상황 통신과 안정적 처리

- Socket.IO를 이용해 학생별 코멘트 생성 현황을 실시간 프론트엔드에 전달, 사용자 경험(UX) 크게 향상
- 비동기 API 호출과 에러 발생 시에도 시스템 부하 최소화 및 빠른 복구 체계 마련
- 세션별 대화 히스토리 관리, System Prompt를 통한 업무 특화 대화 설계

### 문제 해결 및 성능 최적화 경험

- AI 응답 누락, 불필요한 API 호출 문제점 근본 원인 분석 및 프롬프트 강화로 해결
- Token 제한 오류를 방지하기 위해 AI 요청 최대 토큰값 조정 및 기본값 사용
- [Socket.IO](http://socket.io/) 응답 처리 로직 개선으로 Race condition 현상 감소, 오류율 대폭 개선
- 전체 시스템을 선별적으로 리팩토링하여 유지보수성과 확장성 모두 향상

## 주요 성과

- 학생 개별 코멘트 생성 성공률 100% 달성 및 자연스러운 맞춤 응답 완성
- 파일 업로드 기능 도입 후 데이터 입력 오류 30% 감소, 작업 효율 대폭 증가
- SMS 연동 후 학부모 커뮤니케이션 효율 2배 증가, 문자발송 자동화로 업무 시간 60% 절감
- 실제 서비스 환경에서 약 40초 내 6명 학생 분량 코멘트 생성 및 실시간 업데이트 제공

---
## 🛠 기술 스택
- **Language**: TypeScript (ES2016)
- **Runtime**: Node.js + Express
- **AI Engine**: Agentica AI (LLM 기반 의도 해석·도구 선택)
- **Tools**: SmsTool, ExcelTool, StudentExcelTool (typia 스키마)
- **Platform**: 카카오 비즈니스 챗봇 (단일 시나리오·블록·스킬)
- **External APIs**: 메시징 API (SMS/LMS/MMS), 파일 처리
- **Infrastructure**: 환경변수 설정, 정적 파일 서빙, 헬스체크

---

### ⚙️ Tech Stack

#### 🖥️ Frontend

[![React](https://img.shields.io/badge/React-Vite-blue?logo=react)](https://reactjs.org/)  
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.3-blue?logo=tailwind-css)](https://tailwindcss.com/)  
[![Netlify](https://img.shields.io/badge/Deployment-Netlify-green?logo=netlify)](https://www.netlify.com/)

#### ⚙️ Backend

[![Node.js](https://img.shields.io/badge/Node.js-18-green?logo=node.js)](https://nodejs.org/)  
[![Express](https://img.shields.io/badge/Express.js-4.18-lightgrey?logo=express)](https://expressjs.com/)  
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?logo=postgresql)](https://www.postgresql.org/)  
[![Prisma](https://img.shields.io/badge/Prisma-4.15-blue?logo=prisma)](https://www.prisma.io/)  
[![Socket.IO](https://img.shields.io/badge/Socket.IO-4.7-lightgrey?logo=socket.io)](https://socket.io/)  
[![npm](https://img.shields.io/badge/npm-9.8-red?logo=npm)](https://www.npmjs.com/)



## 📄 라이선스 License
이 프로젝트는 ISC License 하에 배포됩니다.

This project is distributed under the **ISC License**.
See the [LICENSE.txt](./LICENSE.txt) file for details.

## 🔍 오픈소스 고지
본 프로젝트에서 사용된 모든 오픈소스 라이브러리의 라이선스 정보는 [NOTICES.md](./NOTICES.md) 파일을 참조하세요.

**Made with using Agentica AI**
---

© 2025 Toribossamdan(토리보쌈단). ISC License.
