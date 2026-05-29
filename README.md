# 🎵 somda — Official Schedule

솜다 공식 공연 스케쥴 웹앱입니다.

---

## 📁 파일 구성

```
index.html   ← 이게 전부예요! 이 파일 하나로 앱이 돌아가요.
README.md    ← 지금 읽고 있는 이 파일
```

---

## 🚀 배포 방법 (GitHub Pages)

### 1단계 — 깃허브 계정 만들기
👉 https://github.com 에서 회원가입 (이미 있으면 패스)

### 2단계 — 새 레포지토리 만들기
1. 로그인 후 오른쪽 위 `+` → `New repository` 클릭
2. Repository name: `schedule` (원하는 이름 OK)
3. **Public** 선택 (Private이면 무료 Pages 안됨!)
4. `Create repository` 클릭

### 3단계 — 파일 올리기
1. 레포 페이지에서 `uploading an existing file` 클릭
2. `index.html`과 `README.md` 끌어다 놓기
3. 아래 `Commit changes` 클릭

### 4단계 — Pages 켜기
1. 레포 → `Settings` 탭
2. 왼쪽 메뉴 → `Pages`
3. Source: `Deploy from a branch`
4. Branch: `main` 선택 → `Save`
5. 1~2분 기다리면 주소 생김!

### 완성된 주소 형태
```
https://[깃허브아이디].github.io/schedule
```

---

## 🔥 Firebase 연결 (팬들도 실시간으로 보려면)

Firebase를 연결하면 내가 관리자 앱에서 공연 추가하면
→ 모든 팬이 즉시 볼 수 있어요!

### Firebase 설정 방법

**1. Firebase 프로젝트 만들기**
1. https://console.firebase.google.com 접속
2. 구글 계정으로 로그인
3. `프로젝트 추가` 클릭
4. 프로젝트 이름 입력 (예: `somda-schedule`)
5. Google Analytics: 선택 안 해도 됨 → `프로젝트 만들기`

**2. 웹 앱 추가**
1. 프로젝트 홈에서 `</>` (웹) 아이콘 클릭
2. 앱 닉네임 입력 → `앱 등록`
3. 아래처럼 생긴 코드가 나와요:

```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "somda-schedule.firebaseapp.com",
  projectId: "somda-schedule",
  storageBucket: "somda-schedule.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

**3. index.html에 붙여넣기**
`index.html` 파일에서 이 부분을 찾아서:
```javascript
const firebaseConfig = {
  apiKey: "여기에-붙여넣기",
  ...
```
위에서 복사한 실제 값으로 교체하세요.

**4. Firestore 데이터베이스 만들기**
1. Firebase 콘솔 왼쪽 메뉴 → `Firestore Database`
2. `데이터베이스 만들기` 클릭
3. `테스트 모드에서 시작` 선택 → `다음` → `사용 설정`

**5. Storage 켜기** (배너 사진 저장용)
1. 왼쪽 메뉴 → `Storage`
2. `시작하기` → `테스트 모드` → `완료`

**6. Storage 보안 규칙 수정**
Storage → `Rules` 탭 → 아래 내용으로 교체:
```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if true;
      allow write: if true;
    }
  }
}
```
(나중에 보안 강화 원하면 별도로 설정)

---

## 🔑 관리자 비밀번호 변경

`index.html` 에서 이 줄을 찾아서:
```javascript
const ADMIN_PW = "somda2026";
```
원하는 비밀번호로 바꾸면 돼요.

---

## 🌐 커스텀 도메인 연결 (선택)

`somda.kr` 같은 도메인 사면 더 예쁜 주소 만들 수 있어요.
- 도메인 구매: 가비아(gabia.com) 또는 Namecheap
- GitHub Pages → Custom domain에 입력
- DNS 설정은 도메인 업체 고객센터에 문의하세요

---

## 💬 문의
앱 관련 문의는 Claude(claude.ai)에게 이 파일 보여주면서 물어보세요!
