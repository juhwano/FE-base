# FE-base

## 기술 스택 (Tech Stack)

- **라이브러리:** React
- **빌드 툴:** Vite
- **스타일링:** Tailwindcss
- **컴포넌트 로직:** Headless UI
- **상태 관리:** Zustand
- **API 통신:** Axios
- **라우팅:** React Router

<br/>

## 요구 사항 (Requirements)

- Node.js 20.19+, 22.12+

<br/>

## 실행 방법 (How to run)

```bash
npm install
npm run dev
```

<br/>

## 시스템 디자인 (System Design)

주요 구성 요소:

- 사용자 인터페이스 (UI): React 컴포넌트 (Pages, Components)
- 라우팅: React Router
- 상태 관리: Zustand 스토어
- API 통신: Axios (Services)
- 백엔드 API: 외부 시스템

상호작용:

- 사용자는 UI와 상호작용합니다.
- UI는 라우팅을 사용하여 페이지 간을 이동합니다.
- UI는 Zustand 스토어에서 상태를 읽고 업데이트합니다.
- UI는 API 통신을 호출하는 액션을 트리거할 수 있습니다.
- API 통신은 백엔드 API와 상호작용하여 요청을 보냅니다.
- 백엔드 API는 API 통신에 응답을 보냅니다.
- API 통신 결과에 따라 Zustand 스토어가 업데이트될 수 있습니다.
- Zustand 스토어는 UI에 상태 업데이트를 제공합니다.

<br/>

## 폴더 구조 (Structure)

```
src/
├── App.jsx             # 메인 애플리케이션 컴포넌트
├── main.jsx            # 애플리케이션 진입점 (React 렌더링 시작)
├── index.css           # 전역 스타일 (Tailwind CSS import 포함)
│
├── assets/             # 이미지, 폰트, 아이콘 등 정적 파일
│   ├── images/
│   ├── fonts/
│   └── icons/
│
├── components/         # 재사용 가능한 UI 컴포넌트 (예: Button, Card, Modal)
│   ├── common/         # 앱 전반에 걸쳐 사용되는 매우 일반적인 컴포넌트
│   │   ├── Button.jsx
│   │   └── Button.module.css # 또는 Tailwind를 직접 사용
│   ├── layout/         # 전체 페이지 구조를 위한 컴포넌트 (Header, Footer, Sidebar)
│   │   ├── Header.jsx
│   │   └── Footer.jsx
│   └── specific/       # 특정 기능이나 페이지에 특화된 컴포넌트 (예: ProductCard)
│       └── ProductCard.jsx
│
├── pages/              # 전체 페이지/뷰를 나타내는 최상위 컴포넌트
│   ├── HomePage.jsx
│   ├── AboutPage.jsx
│   ├── auth/           # 특정 기능(예: 인증)과 관련된 페이지들을 그룹화
│   │   ├── LoginPage.jsx
│   │   └── RegisterPage.jsx
│   └── user/
│       └── ProfilePage.jsx
│
├── services/           # 외부 API와 통신하는 함수들 (Axios 사용)
│   ├── authService.js  # 인증 관련 API 호출 함수들
│   ├── userService.js  # 사용자 관련 API 호출 함수들
│   └── api.js          # Axios 인스턴스 또는 기본 API 설정
│
├── store/              # Zustand를 이용한 전역 상태 관리 스토어
│   ├── authStore.js    # 인증 관련 상태
│   ├── userStore.js    # 사용자 관련 상태
│   └── index.js        # 모든 스토어를 통합/내보내기
│
├── utils/              # 헬퍼 함수, 상수, 컴포넌트와 무관한 로직
│   ├── constants.js    # 애플리케이션 전반에 사용되는 상수
│   ├── helpers.js      # 일반적인 유틸리티 함수 (예: formatDate, validateEmail)
│   └── validators.js   # 유효성 검사 로직
│
└── hooks/              # 재사용 가능한 로직을 위한 커스텀 React Hooks
    ├── useAuth.js
    └── useDebounce.js
```

**각 디렉토리에 대한 설명:**

- **`src/`**: 모든 소스 코드의 루트 디렉토리입니다.
- **`assets/`**: 이미지, 폰트, 아이콘 등 직접 제공되거나 임포트되는 정적 파일들을 저장합니다.
- **`components/`**:
  - 모든 재사용 가능한 UI 컴포넌트들을 담습니다.
  - `common` (매우 일반적이고 앱 전반에 사용), `layout` (페이지 구조용), `specific` (특정 기능이나 페이지에 묶인 컴포넌트) 등으로 세분화할 수 있습니다.
  - 각 컴포넌트는 일반적으로 자체 폴더를 가지며, 그 안에 `.jsx` 파일과 필요시 자체 CSS 모듈 또는 테스트 파일을 포함합니다.
- **`pages/`**:
  - 애플리케이션의 전체 페이지 또는 뷰에 해당하는 최상위 컴포넌트들을 나타냅니다.
  - 대부분 React Router 설정의 라우트와 직접적으로 매핑됩니다.
  - 더 큰 애플리케이션의 경우 기능별로 그룹화할 수 있습니다 (예: `auth/`, `user/`).
- **`services/`**:
  - API 호출(Axios 사용)을 담당하는 함수들을 포함합니다.
  - 각 파일은 일반적으로 관련 API 호출을 그룹화합니다 (예: `authService.js`는 로그인/로그아웃/회원가입 관련).
  - `api.js`는 Axios 인스턴스(기본 URL, 인터셉터 등)를 설정하는 데 사용될 수 있습니다.
- **`store/`**:
  - Zustand 스토어 전용 디렉토리입니다.
  - 각 파일은 전역 상태의 개별적인 부분을 나타낼 수 있습니다.
  - `index.js`를 사용하여 모든 스토어를 더 쉽게 임포트할 수 있도록 내보낼 수 있습니다.
- **`utils/`**:
  - 순수 JavaScript 헬퍼 함수, 상수, 그리고 API와 직접 상호작용하거나 상태를 관리하지 않는 기타 비-컴포넌트 로직을 위한 디렉토리입니다.
- **`hooks/`**:
  - 커스텀 React Hooks를 위한 디렉토리입니다. 이들은 여러 컴포넌트에서 상태 저장 로직을 재사용할 수 있게 해주는 함수입니다.

<br/>
