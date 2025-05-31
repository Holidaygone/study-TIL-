# SSAFY WithView 프로젝트 복기 및 기술 스택 심화 학습

## 1. 프로젝트 개요 및 학습 목표
SSAFY 2학기 웹/앱 개발 프로젝트 "WithView" 복기 및 사용 기술 스택 심화 학습 기록.
(당시 React, 웹소켓 등은 정규 교육과정 외 독학으로 진행했으므로, 학습 과정 및 적용 내용을 중점적으로 기록)

## 2. 주요 기술 스택
- React.js
- Redux Toolkit (상태 관리)
- axios (HTTP 통신)
- @stomp/stompjs & sockjs-client (웹소켓 통신)
- react-slick (캐러셀 UI)
- react-cropper (이미지 크롭)
- react-modal, react-popover (UI 컴포넌트)
- Bulma (CSS 프레임워크)

## 3. 핵심 기능별 상세 복기

### 3.1 웹소켓을 이용한 실시간 통신
- **역할:** 서버 내 채널별 실시간 인원 수 업데이트, 1대1 채팅 기능 구현의 기반
- **사용 라이브러리:** `@stomp/stompjs`, `sockjs-client`
- **개념 복기:**
    - 웹소켓이란? HTTP와의 차이점 (양방향, 지속 연결), 왜 실시간 서비스에 필요한가?
    - STOMP 프로토콜? 웹소켓 위에서 메시징 규칙을 제공 (Pub/Sub 모델)
    - `SockJS`의 역할? (하위 호환성/fallback)
- **코드 분석 (`Serverpage.jsx` 예시):**
    - `stomp.connect()`: 웹소켓 연결 시 인증(userSeq) 전달
    - `stomp.subscribe(\`/api/sub/server/${serverSeq}\`)`: 특정 서버 주제 구독 -> 메시지 수신 (`recvMessage`)
    - `stomp.send(\`/api/pub/server/${serverSeq}/enter\`)`: 서버 입장 알림 발행
    - `recvMessage(data)`: 받은 메시지(`channelState`)로 React 상태 업데이트 -> UI 반영
- **고민/해결:**
    - [이 부분에 웹소켓 연결 안정성, 재연결, 구독 해제 등 본인이 겪었던 문제와 해결 과정을 기록]

### 3.2 이미지 크롭 및 업로드
- **역할:** 사용자 프로필/채널 배경 이미지 업로드 시 클라이언트 단에서 편집 기능 제공
- **사용 라이브러리:** `react-cropper`
- **개념 복기:**
    - `FileReader`, `Blob`, `FormData`, `multipart/form-data`
    - 클라이언트에서 이미지 처리하는 이유 (서버 부하 감소, UX 향상)
- **코드 분석 (`Serverpage.jsx` 예시):**
    - `handleImageChange`: `FileReader`로 파일 읽어 `setCroppedImage` (Base64)
    - `cropperRef.current.cropper.getCroppedCanvas().toBlob()`: 크롭된 이미지 `Blob` 변환
    - `new File([blob], "newFile.png", { type: blob.type })`: Blob으로 파일 객체 생성
    - `formData.append("file", file)`: `FormData`에 파일 추가하여 `axiosInstance`로 전송
- **고민/해결:**
    - [이미지 용량 최적화, 이미지 비율 유지 등 겪었던 문제와 해결 과정 기록]

### 3.3 React 상태 관리 (Redux Toolkit)
- **역할:** 사용자 정보(토큰, 닉네임, 프로필), 웹소켓 객체 등 전역 상태 관리
- **사용 라이브러리:** `react-redux`, `redux-toolkit`
- **개념 복기:**
    - Redux의 필요성? (컴포넌트 간 복잡한 데이터 전달 해결, 상태 예측 가능)
    - `useSelector`, `useDispatch` 사용법
- **코드 분석:**
    - `useSelector((state) => state.user.nickname)` 등 활용
- **고민/해결:**
    - [새로고침 시 상태 유지, 비동기 데이터 관리 등 겪었던 문제와 해결 과정 기록]

## 4. 학습 회고 및 얻은 점
- SSAFY 정규 교육 외 독학을 통해 React, 웹소켓 등 새로운 기술 스택을 빠르게 습득하고 실제 프로젝트에 적용하는 경험.
- [유니티 프로젝트 우수상 수상 경험 간략 언급 및 웹/앱 개발로의 확장 가능성 제시]
- 주도적인 문제 해결 능력과 학습 능력 향상.