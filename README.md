# FPPL 연구실 홈페이지

경희대학교 식품가공·포장 연구실(Food Processing & Packaging Lab) 홈페이지입니다.
서버나 데이터베이스가 없는 정적 사이트라서, 파일만 올려두면 동작하고 따로 관리할 서버가 없습니다.

## 폴더 구성

```
index.html            사이트 전체 (디자인 + 내용)
images/
  logo/               경희대·FPPL 로고
  people/             교수님·구성원 사진
  gallery/            갤러리 사진
  news/               소식 사진
  research/           연구분야 대표 논문 그림
README.md             이 안내서
```

미리 보기: `index.html`을 더블클릭하면 브라우저에서 바로 열립니다.

## 게시 현황

- 사이트 주소: https://fppl-khu.github.io
- GitHub 조직 `fppl-khu`의 저장소 `fppl-khu.github.io`에 있으며, 이 저장소에 파일을 올리면 1–2분 뒤 사이트에 자동 반영됩니다.
- 관리자 추가·인수인계: 조직 페이지 **People → Invite member**에서 새 관리자를 **Owner**로 초대합니다. 각자 개인 계정으로 로그인하므로 공유 비밀번호가 없습니다. 담당자가 졸업하면 다음 담당자를 Owner로 추가한 뒤 빠지면 됩니다.

학교 주소(예: `fppl.khu.ac.kr`)나 별도 도메인을 연결하려면: 조직 **Settings → Pages**에서 도메인 소유 확인(TXT)을 시작하고, 저장소 **Settings → Pages → Custom domain**에 주소를 입력한 뒤, 정보처(또는 도메인 업체)에 `CNAME fppl-khu.github.io`와 TXT 레코드 등록을 요청합니다. 반영 후 **Enforce HTTPS**를 켭니다.

## 내용 고치기

GitHub에서 `index.html`을 열고 연필 아이콘(Edit)을 누르면 브라우저에서 바로 고칠 수 있습니다. 저장(Commit changes)하면 1–2분 뒤 사이트에 반영되고, 수정 기록이 남아 언제든 되돌릴 수 있습니다.

내용은 모두 `index.html` 안의 `const LAB = {` 부분에 모여 있습니다. Ctrl+F로 아래 단어를 찾으면 됩니다. 디자인 코드는 건드리지 않아도 됩니다.

- 글은 모두 `{ ko: "한국어", en: "English" }` 형태로 두 언어를 함께 적습니다.
- `[예시]` / `[Example]`로 시작하는 글은 사이트에 주황색으로 표시되는 임시 내용입니다. 실제 내용으로 바꾸거나 줄을 지우세요.
- 각 줄 끝의 쉼표(`,`)를 지우지 않도록 주의하세요. 고친 뒤 사이트가 하얗게 나오면 대개 쉼표나 따옴표가 빠진 것입니다.

### 구성원 추가·이동 — `members:` 를 찾기

기존 줄을 복사해서 이름만 바꿉니다.

```js
{ group: "ms", name: { ko: "홍길동", en: "Gildong Hong" }, initials: "GH", photo: "images/people/gildong.jpg", pos: { ko: "석사과정", en: "M.S. student" }, year: "2027", research: { ko: "활성 포장", en: "Active packaging" } },
```

- `group`: `researcher`(연구교수·박사후연구원) / `phd`(석박통합) / `ms`(석사) / `alumni`(졸업생)
- 졸업하면 `group`을 `alumni`로, `pos`를 `석사 졸업`으로 바꾸고, `year`에 졸업연도, `workplace`에 근무처를 적습니다.
- 사진이 없으면 `photo`를 빼면 이니셜(`initials`)이 대신 나옵니다.

### 소식 추가 — `news:` 를 찾기

맨 위에 한 줄 추가합니다 (위에서부터 최신순).

```js
{ date: "2027.03", tag: "award", text: { ko: "홍길동 석사과정, 한국포장학회 우수발표상 수상", en: "Gildong Hong wins a best presentation award at KOPAST" } },
```

`tag`: `award`(수상) / `lab`(연구실) / `media`(언론) / `story`(학생 이야기)

### 갤러리 사진 추가 — `gallery:` 를 찾기

사진을 `images/gallery/`에 올리고 한 줄 추가합니다.

```js
{ src: "images/gallery/2027-05-conference.jpg", date: "2027.05", category: "event", caption: { ko: "한국식품과학회 발표", en: "KoSFoST annual meeting" } },
```

`category`: `lab`(연구실) / `event`(학회·행사) / `media`(언론·인터뷰). 사진은 가로 1600px 이하 JPG로 줄여서 올리면 사이트가 빨라집니다.

### 논문 추가 — `publications:` 를 찾기

맨 앞에 한 줄 추가합니다. `doi`를 적으면 제목에 논문 링크가 걸립니다.

```js
{"year": 2027, "type": "Article", "title": "논문 제목", "authors": "Hong, G., ... & Kim, J. T.", "source": "Food Hydrocolloids. 160, 110000", "doi": "10.1016/j.foodhyd.2027.110000"},
```

### 연구분야·대표 논문 — `areas:` 를 찾기

분야마다 `deep`(연구 배경·방법·대표 연구)과 `paper`(대표 논문)가 있습니다. 대표 논문 그림을 바꾸려면 `images/research/`의 같은 이름 파일을 교체하거나, `paper`의 `fig`에 새 경로를 적습니다. `impact`는 IF 값입니다.

### 사진만 바꾸기

`images/` 안의 파일을 **같은 이름**으로 덮어쓰면 됩니다 (GitHub에서 Add file → Upload files로 같은 이름 파일을 올리면 교체됨).
