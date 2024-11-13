# React2

**학번:** 202030326  
**이름:** 이하늘

---

## 수업 내용 정리

### 2024년 11월 06일 수업 내용

#### Styled JSX
- **Styled JSX**는 CSS-in-JS 라이브러리로, 내장 모듈이기 때문에 별도의 설치가 필요 없습니다.
- 자바스크립트를 사용하여 CSS 속성을 지정할 수 있는 라이브러리입니다.

#### CSS-in-JS의 단점
1. **개발 도구 지원 부족:**
   - IDE나 코드 편집기에서 문법 하이라이팅, 자동 완성, 린트(lint) 기능을 제공하지 않습니다.
2. **의존성 증가:**
   - 코드 내에서 CSS에 대한 의존성이 커져 앱 번들이 커지고 성능이 저하됩니다.
3. **성능 문제:**
   - 서버에서 미리 CSS를 생성해도 클라이언트에서 React 하이드레이션 후 CSS를 다시 생성해야 합니다.
   - 기능 추가 시 실행 시점 부하가 증가하여 웹 앱이 느려집니다.

#### CSS Module
- **CSS Module**은 CSS-in-JS의 단점을 회피하기 위한 좋은 방법입니다.
- 클래스는 컴포넌트 스코프를 가지며, 고유한 이름으로 충돌을 방지합니다.
- 전역 CSS를 선언하려면 `/styles/globals.css`를 만들고 `_app.js`에 import 합니다.
- `:global` 키워드를 사용하여 특정 클래스에 전역 스타일을 적용할 수 있습니다.

#### SASS
- **SASS**는 Next.js에서 기본으로 지원하는 전처리기입니다.
- 설치: `npm install sass`
- SASS 및 SCSS 문법으로 CSS Module을 생성하고 사용할 수 있습니다.
- 파일 확장자를 `.scss`로 변경하면 됩니다.
- 기본 설정을 변경하려면 `next.config.js` 파일을 수정합니다.

---

### 2024년 10월 30일 수업 내용

#### 서버가 데이터 불러오기
- 서버는 두 가지 방법으로 HTTP 요청을 처리할 수 있습니다:
  1. **Node의 내장 HTTP 라이브러리:** 설정 및 처리가 복잡합니다.
  2. **HTTP 클라이언트 라이브러리 (예: Axios):** 설정이 간편하고 널리 사용됩니다.
- **Axios**는 클라이언트와 서버 모두에서 동일하게 사용할 수 있으며, 널리 사용되어 신뢰성이 높습니다.

#### REST API 사용하기
- REST API 호출 시 **Public API**와 **Private API**를 구분해야 합니다.
- **Public API:** 인증이나 권한이 필요 없습니다.

#### GraphQL API
- **GraphQL**은 2012년 페이스북에서 개발되었으며, REST나 SOAP과는 다른 질의어를 사용하여 API 데이터를 다룹니다.

#### REST API 개요
- **REST (Representational State Transfer):** 자원을 이름으로 구분하여 그 자원의 상태를 통신을 통해 주고받는 아키텍처 스타일입니다.

#### Json Server
- 백엔드 개발 전 또는 외부 API가 결정되지 않았을 때 로컬에 **Json Server**를 구축하여 프론트엔드 개발에 활용할 수 있는 Node 패키지입니다.
- 설치: `npm install -g json-server`

#### Axios 란?
- **Axios**는 Next.js에서 REST API를 다룰 때 주로 사용되는 라이브러리입니다.
- **장점:**
  - 간편한 문법: 기본적으로 JSON 데이터를 다룹니다.
- **Fetch API와의 비교:**
  - **Fetch API:** 내장 API로 별도 설치가 필요 없고, Promise 기반이며 스트림 처리가 가능합니다.
  - **Axios:** 복잡한 요청이나 에러 처리가 용이합니다.

#### Axios 설치 및 사용
- 설치: `npm install axios`
- 사용 시 `axios.get()`을 통해 응답 객체(res)를 받아옵니다.
- 비동기 데이터 로딩과 상태 관리를 위해 `useState`와 `useEffect`를 사용하여 로딩 상태를 처리하고 조건부 렌더링을 구현합니다.

---

### 2024년 10월 23일 수업 내용

#### Static Resource 관리
- **이미지 파일**은 SEO에 큰 영향을 미치며, 다운로드 시간과 누적 레이아웃 이동(CLS)에 영향을 줍니다.
- **Next.js Image 컴포넌트**를 사용하여 CLS 문제를 해결할 수 있습니다.
  - **기능:**
    - Lazy loading
    - 이미지 사이즈 최적화
    - Placeholder 제공
    - 최신 이미지 포맷 지원 (webP 등)
- 정적 자원은 기본적으로 `public` 디렉토리에 저장합니다.

#### Image Component - Remote
- 외부 이미지를 사용하려면 `next.config.mjs`에 해당 URL을 추가해야 합니다.

#### 코드 구성과 데이터 불러오기
- **디렉토리 구조:**
  - `node_modules/`: 의존성 패키지
  - `pages/`: 페이지 파일 및 라우팅 관리
  - `public/`: 정적 자원 (CSS, JS, 이미지 등)
  - `styles/`: 스타일링 모듈 (CSS, SASS 등)
- **컴포넌트 구성:** 아토믹 디자인 원칙에 따라 `atoms`, `molecules`, `organisms`, `templates`로 구성
- **유틸리티 구성:** `utilities/` 디렉토리에 컴포넌트가 아닌 스크립트 관리
- **lib 파일 구성:** 서드파티 라이브러리를 감싸는 스크립트는 `lib/` 디렉토리에 관리

#### 데이터 불러오기
- Next.js에서는 클라이언트와 서버 모두에서 데이터를 불러올 수 있습니다.
  - **정적 페이지 생성:** `getStaticProps`를 사용하여 빌드 시점에 데이터 불러오기
  - **서버 사이드 렌더링:** `getServerSideProps`를 사용하여 요청 시점에 데이터 불러오기

---

### 2024년 10월 2일 수업 내용

#### 초기 설정 및 프로젝트 생성
- **환경 설정:**
  - PowerShell에서 Chocolatey 설치
  - Git 설치: `choco install git`
  - Node.js 및 npm, npx 버전 확인
- **프로젝트 생성:**
  - `npx create-next-app@latest` 명령어로 Next.js 프로젝트 생성
  - 프로젝트 이름과 설정 선택 후 설치 완료
- **프로젝트 구조:**
  - `pages/`와 `src/` 디렉토리 구조 이해
  - 라우팅 및 페이지 생성 방법 학습

---

### 2024년 9월 25일 수업 내용

#### Next.js의 기능 및 최적화
- **라우팅 시스템:**
  - Next.js는 파일 시스템 기반 라우팅을 사용합니다.
  - `pages/` 디렉토리 내의 파일이 자동으로 라우트됩니다.
- **페이지 간 이동 최적화:** 클라이언트 사이드 네비게이션을 통해 빠른 페이지 전환
- **정적 자원 제공:** Next.js의 정적 자원 제공 방식 이해
- **Image 컴포넌트:** 자동 이미지 최적화 및 다양한 최적화 기법 사용
- **HTML 메타데이터 처리:** 컴포넌트 내에서 메타데이터 관리
- **커스터마이징:** `_app.js`와 `_document.js` 파일의 역할 및 커스터마이징 방법

#### 랜더링 전략
1. **서버 사이드 랜더링 (SSR):**
   - 각 요청마다 페이지를 동적으로 랜더링
   - **장점:** 보안성, SEO 최적화, 다양한 클라이언트 환경 지원
   - **단점:** 서버 부하 증가, 요청 처리 시간 길어짐
2. **클라이언트 사이드 랜더링 (CSR):**
   - 클라이언트에서 페이지 랜더링
   - **장점:** 네이티브 앱 같은 사용자 경험, 쉬운 페이지 전환, 서버 부하 감소
   - **단점:** 초기 로딩 시 빈 화면, SEO 어려움
3. **정적 사이트 생성 (SSG):**
   - 빌드 시점에 페이지를 미리 랜더링
   - **장점:** 뛰어난 성능, 쉬운 확장, 보안성
   - **단점:** 콘텐츠 업데이트 시 재빌드 필요
4. **증분 정적 재생성 (ISR):**
   - SSG의 단점을 보완하여 일정 시간 간격으로 페이지를 재랜더링
   - 예: 데이터가 자주 변하지 않는 페이지에 적합

---

### 2024년 9월 11일 수업 내용

#### 추가 설정 및 오류 해결
- **타입스크립트 설정:** 프로젝트 생성 시 타입스크립트 선택 또는 설정 파일 추가
- **웹팩 설정:**
  - `next.config.js` 파일을 통해 기본 웹팩 설정 변경 가능
  - 서버 사이드 랜더링 시 발생할 수 있는 오류 해결 방법 학습
- **Transpile 과정:**
  - **Babel vs SWC:**
    - **Babel:** 코드 변환이 느리고 변환 코드가 복잡함
    - **SWC:** Next.js 12부터 기본 사용, 빠르고 효율적
- **동적 컴포넌트 로딩:**
  - `useEffect` 훅이나 `dynamic` 함수를 사용하여 클라이언트 사이드에서만 컴포넌트 로딩
- **코드 예제:**
  - Highlight.js 라이브러리 사용 시 서버와 클라이언트에서의 문제 해결 방법

#### 서버 사이드 랜더링 (SSR) vs 클라이언트 사이드 랜더링 (CSR) vs 정적 사이트 생성 (SSG)
- **SSR의 장점:** 보안성, SEO 최적화, 다양한 클라이언트 환경 지원
- **SSR의 단점:** 서버 부하 증가, 요청 처리 시간 길어짐
- **CSR의 장점:** 네이티브 앱 같은 사용자 경험, 쉬운 페이지 전환, 서버 부하 감소
- **CSR의 단점:** 초기 로딩 시 빈 화면, SEO 어려움
- **SSG의 장점:** 뛰어난 성능, 쉬운 확장, 보안성
- **SSG의 단점:** 콘텐츠 업데이트 시 재빌드 필요

---

### 2024년 9월 4일 수업 내용
## 1. 기본 환경 설정

### 1.1 PowerShell 관리자 권한으로 실행

1. **PowerShell을 관리자 권한으로 실행**합니다.
    - 시작 메뉴에서 "PowerShell"을 검색한 후, 마우스 오른쪽 버튼을 클릭하고 "관리자 권한으로 실행"을 선택합니다.

### 1.2 Chocolatey 설치

1. **Chocolatey**를 설치하기 위해 다음 명령어를 입력합니다:

    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; `
    [System.Net.ServicePointManager]::SecurityProtocol = `
    [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
    iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```

2. 설치가 완료되면 **Chocolatey 버전**을 확인하여 설치가 정상적으로 되었는지 확인합니다:

    ```powershell
    choco -v
    ```

### 1.3 Git 설치

1. **Chocolatey**를 사용하여 **Git**을 설치합니다. 다음 명령어를 실행합니다:

    ```powershell
    choco install git
    ```

2. 설치가 완료되면 Git 버전을 확인하여 정상 설치를 확인합니다:

    ```bash
    git --version
    ```

### 1.4 Node.js 및 NPM 버전 확인

1. **Node.js**, **NPM**, **npx**의 설치 및 버전을 확인합니다:

    ```bash
    node -v
    npm -v
    npx -v
    ```

    - 각 명령어가 버전을 출력하면 정상적으로 설치된 것입니다.

## 2. 추가 설정 (선택 사항)

- **Visual Studio Code**를 ZIP 파일로 다운로드 받아 D 드라이브에 옮깁니다.
    - 교수님의 진도에 맞추기 위한 설정으로, 필요에 따라 선택적으로 수행합니다.

## 3. 프로젝트 설정

### 3.1 프로젝트 폴더 생성

- 원하는 드라이브(C 드라이브 또는 D 드라이브)에 프로젝트를 위한 폴더를 생성합니다.

### 3.2 Create React App 전역 설치

- **Create React App**을 전역으로 설치합니다:

    ```bash
    npm install -g create-react-app
    ```

### 3.3 Next.js 프로젝트 생성 (Page Router)

1. **Next.js** 프로젝트를 생성합니다:

    ```bash
    npx create-next-app@latest
    ```

2. **프로젝트 이름**을 `page-router`로 입력합니다.

3. 설치 과정에서 차례대로 다음과 같이 응답합니다:
    - **Yes**: 프로젝트 루트에 설치
    - **No**
    - **No**
    - **No**
    - **Yes**

### 3.4 개발 서버 실행

1. 생성된 `page-router` 폴더로 이동합니다:

    ```bash
    cd page-router
    ```

2. 개발 서버를 실행합니다:

    ```bash
    npm run dev
    ```

3. 기본 브라우저로 열리며, 만약 **Microsoft Edge**로 열리면 **기본 앱 설정**을 변경하여 **Chrome**으로 변경할 수 있습니다.

### 3.5 페이지 파일 수정

1. `index.js` 파일을 복사하여 `about.js`로 이름을 변경합니다.

2. `about.js`의 21번째 줄을 `about.js`로 수정합니다.

### 3.7 개발 서버 실행

1. 생성된 `app-router` 폴더로 이동합니다:

    ```bash
    cd app-router
    ```

2. 개발 서버를 실행합니다:

    ```bash
    npm run dev
    ```

### 3.8 페이지 파일 수정

1. `page.js` 파일을 복사하여 `about.js`로 이름을 변경한 후 다시 원래대로 변경합니다.

2. `src/app/about` 폴더를 생성하고 `about.js` 파일을 넣습니다.

3. 파일 이름을 `page.js`로 재변경합니다.

4. `page.js` 파일의 2번째 줄을 확인합니다:

    ```javascript
    import styles from "../page.module.css";
    ```

5. 10번째 줄을 확인합니다:

    ```javascript
    <code className={styles.code}>src/app/about/page.js</code>
    ```

## 4. 추가 프로젝트 생성

1. 다시 D 드라이브로 돌아갑니다.

2. **Next.js**의 예제 프로젝트를 생성합니다:

    ```bash
    npx create-next-app --example blog-starter
    ```

3. **프로젝트 이름**을 `my-blog`로 입력합니다.

4. 생성된 `my-blog` 폴더를 엽니다.

5. Git Bash에서 다음 명령어로 개발 서버를 실행합니다:

    ```bash
    npm run dev
    ```

6. 브라우저에서 열리는 것을 확인합니다.

## 5. 참고 자료

- [Vercel GitHub](https://github.com/vercel)