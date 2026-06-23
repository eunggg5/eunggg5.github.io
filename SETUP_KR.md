# Eunji의 개인 셋업 가이드 🎵

이 폴더에는 al-folio 학술 포트폴리오 템플릿이 본인 콘텐츠로 채워져 있어요.
아래 순서대로 따라 하시면 `eunjioh.com`에 새 사이트가 뜹니다.

---

## 1단계 — GitHub에 코드 올리기

### 1-1. GitHub에 새 빈 저장소(repo) 만들기

1. https://github.com/new 접속
2. Repository name: **`eunggg5.github.io`** 으로 정확히 입력 (이렇게 하면 무료 호스팅이 깔끔해져요)
3. **Public** 선택
4. ⚠️ "Add a README file", ".gitignore", "license" 옵션은 **체크하지 마세요** (이미 다 있어요)
5. "Create repository" 클릭

### 1-2. 로컬 코드를 GitHub로 푸시

터미널을 열고, 이 폴더로 이동한 다음:

```bash
cd /Users/user/workspace/EunJi-Oh-website

# 본인 이름/이메일 git에 설정 (한 번만)
git config user.name "Eunji Oh"
git config user.email "eoh61@gatech.edu"

# 모든 변경사항 커밋
git add -A
git commit -m "Customize al-folio for Eunji Oh"

# 본인 GitHub 저장소를 origin으로 등록
git remote add origin https://github.com/eunggg5/eunggg5.github.io.git

# 푸시 (처음엔 GitHub 로그인 창이 뜰 수 있어요)
git branch -M main
git push -u origin main
```

푸시할 때 비밀번호 대신 **Personal Access Token**을 요구해요:
- GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token
- Scope: `repo` 만 체크하고 생성 → 토큰 복사
- 터미널에 password 자리에 그 토큰 붙여넣기

---

## 2단계 — GitHub Pages 활성화

푸시 후 GitHub Actions가 자동으로 빌드를 시작합니다 (~3-5분).

1. 저장소 페이지로 가서 **Actions** 탭 클릭 → "Deploy site" 워크플로우가 초록색 ✓ 될 때까지 기다림
2. 빌드가 끝나면 자동으로 `gh-pages` 브랜치가 생김
3. **Settings → Pages**:
   - Source: **Deploy from a branch**
   - Branch: **`gh-pages`** / `(root)` 선택 → Save
4. 1-2분 뒤 `https://eunggg5.github.io` 에 사이트가 뜹니다 ✅

---

## 3단계 — `eunjioh.com` 도메인 연결 (Wix → GitHub Pages)

⚠️ **중요**: 이 단계는 기존 Wix 사이트가 `eunjioh.com` 에서 보이지 않게 됩니다 (도메인이 새 사이트로 이전).
Wix 사이트 자체는 삭제되지 않고 백업으로 남아있어요. 결과 마음에 들면 그때 진행하세요.

### 3-1. Wix 사이트와 도메인 연결 끊기

1. Wix 대시보드 → 본인 사이트 → **Settings → Domains**
2. `eunjioh.com` 옆 **Manage** → **Disconnect this domain** (또는 "Move to another site")
3. 도메인은 그대로 본인 소유 (구매한 거니까), Wix 사이트와의 *연결*만 끊김

### 3-2. DNS 레코드 GitHub Pages로 설정

Wix 대시보드 → **Domains → eunjioh.com → Manage → Advanced (또는 DNS Records)**

기존 A 레코드 / CNAME 다 지우고, 아래 4개 A 레코드와 1개 CNAME 추가:

| Type  | Host (Name) | Value                                  | TTL |
|-------|-------------|----------------------------------------|-----|
| A     | @           | 185.199.108.153                        | 1h  |
| A     | @           | 185.199.109.153                        | 1h  |
| A     | @           | 185.199.110.153                        | 1h  |
| A     | @           | 185.199.111.153                        | 1h  |
| CNAME | www         | eunggg5.github.io                      | 1h  |

### 3-3. GitHub Pages 쪽에서 도메인 확정

1. 저장소 → Settings → Pages → **Custom domain** 칸에 `eunjioh.com` 입력 → Save
   (이미 `CNAME` 파일이 있어서 자동으로 들어가 있을 수도 있음)
2. DNS 전파 후 **Enforce HTTPS** 체크박스가 뜨면 체크 (인증서 자동 발급, 보통 10분~1시간 걸림)

### 3-4. 확인

`https://eunjioh.com` 접속 → 새 al-folio 사이트가 떠야 합니다 🎉

DNS 전파에 최대 24시간 걸리는데, 보통 30분~2시간이면 됩니다.

---

## 4단계 — 콘텐츠 다듬기

### 자주 수정하는 파일들

| 무엇을 바꾸려면        | 어떤 파일                             |
|------------------------|---------------------------------------|
| 자기소개·학력          | `_pages/about.md`                     |
| 프로필 사진            | `assets/img/prof_pic.jpg` (덮어쓰기)  |
| 사이트 제목·설명·이메일| `_config.yml` 상단                    |
| 소셜 링크 (구글스칼라 등)| `_data/socials.yml`                 |
| 논문 추가              | `_bibliography/papers.bib` 에 BibTeX 한 칸 추가 |
| 프로젝트 추가          | `_projects/` 폴더에 새 .md 파일       |
| Conference Overview 글 | `_posts/YYYY-MM-DD-title.md` 추가     |
| CV PDF                 | `assets/pdf/EunjiOh_CV.pdf` 로 본인 CV 업로드 |
| CV 페이지 내용         | `_data/cv.yml` (구조화된 CV)          |
| 홈 우측 알림(News)     | `_news/` 폴더에 새 .md 파일           |

### 수정 후 사이트에 반영하기

```bash
git add -A
git commit -m "Update bio"  # 적당한 메시지
git push
```

푸시 후 ~3분 뒤 자동으로 사이트가 업데이트됩니다.

---

## 5단계 (선택) — 로컬에서 미리보기

빌드 결과를 GitHub 푸시 없이 컴퓨터에서 바로 보려면 Docker가 가장 쉬워요:

1. Docker Desktop 설치: https://www.docker.com/products/docker-desktop/
2. 이 폴더에서:
   ```bash
   docker compose up
   ```
3. 브라우저에서 `http://localhost:8080` 열면 미리보기

이 기능은 *선택*입니다. 안 쓰고 GitHub 푸시로만 확인해도 됩니다.

---

## 도움 필요할 때

- al-folio 공식 문서: https://github.com/alshedivat/al-folio
- 자주 묻는 질문(영문): 같은 저장소의 `docs/FAQ.md`

문제 생기면 Claude한테 "사이트 배포에서 X 에러가 떠" 하고 물어보세요 — 스크린샷이나 에러 메시지 첨부하면 더 좋고.
