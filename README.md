# Quick Draw 프론트앤드

## 프로젝트 개요
React 기반 SPA로, 사용자가 그림을 그리고 머신러닝 모델로 인식 결과를 확인하는 낙서 애플리케이션

## 주요 구조 및 컴포넌트

## 사용 기술
- React, styled-components
- React Router
- Context API
- Canvas API
- Fetch API (서버 통신)

### components
-**Canvas**
- canvas 요소를 스타일링하여 출력
- 외부에서 전달 된 callback 함수로 ref 접근 가능
-**Direction**
- 사용자에게 어떤 대상을 그려야 하는지 안내
- category 값을 기반으로 안내 문구 출력
-**Result**
- 사용자가 그림을 제출했을 때 모델의 예측 결과를 보여줌
- 로딩 상태 표시 및 재도전 기능 포함
- 제출 (onClick), 다시(onRefresh) 버튼과 예측 결과 시각화 포함

### container
- **DrawContainer**
  - 사용자가 마우스로 그림을 그린 후 머신러닝 모델에 예측 요청하고 결과를 화면에 출력하는 전체 흐름 담당
  - 랜덤 카테고리 제시 (`Direction`)
  - 사용자 마우스 기반 드로잉 기능 (`Canvas`)
  - 이미지 → 서버 전송 → 예측 결과 출력 (`Result`)
  - [제출], [다시] 버튼 인터랙션 처리

  ### pages
- **DrawPage**
  - 사용자가 실제로 낙서를 수행하고 결과를 확인하는 페이지
  - `Helmet` 으로 페이지 타이틀 "낙서하기" 설정
  - `Wrapper` 로 레이아웃 가운데 정렬
  - 핵심 드로잉 인터페이스인 `DrawContainer` 포함

### member
- **LoginForm**
  - 이메일과 비밀번호 입력을 처리하는 로그인 UI 컴포넌트
- **LoginContainer**
  - 로그인 상태 및 유효성 검사 관리
  - 인증 성공 시 전역 상태(CommonContext) 갱신 및 리다이렉션
  - React 훅 사용: `useState`, `useCallback`, `useSearchParams`, `useNavigate`, `useContext`

### main/pages
- **MainPage**
  - 앱 첫 화면
  - 메인 이미지와 시작하기 버튼 제공
  - 시작하기 클릭 시 그리기 페이지로 이동

