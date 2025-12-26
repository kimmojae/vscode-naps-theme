# Deploy Guide

Naps Theme을 VSCode Marketplace와 Open VSX에 배포하는 가이드입니다.

## 사전 준비 (최초 1회)

### 1. CLI 도구 설치

```bash
npm install -g @vscode/vsce
npm install -g ovsx
```

### 2. VSCode Marketplace 설정

1. [Azure DevOps](https://dev.azure.com) 가입 (GitHub 계정으로 가능)
2. User Settings → Personal Access Tokens → New Token
   - Organization: `All accessible organizations`
   - Scopes: `Marketplace > Manage` 체크
   - Expiration: 1년 권장
3. 토큰 복사해두기
4. Publisher 로그인:
   ```bash
   vsce login kimmojae
   # 토큰 입력
   ```

### 3. Open VSX 설정

1. [Open VSX](https://open-vsx.org) 접속
2. GitHub 로그인 → Eclipse Foundation 계정 연동
3. Publisher Agreement 서명
4. Namespaces → Create Namespace → `kimmojae`
5. Settings → Access Tokens → Generate
6. 토큰 복사해두기

---

## 배포하기

### Step 1: 버전 업데이트

`package.json`:
```json
"version": "0.2.0"
```

`CHANGELOG.md`:
```markdown
### **0.2.0**

- 변경 내용
```

### Step 2: 커밋

```bash
git add .
git commit -m "Release v0.2.0"
git push
```

### Step 3: VSCode Marketplace 배포

```bash
vsce publish
```

### Step 4: Open VSX 배포

```bash
ovsx publish -p <토큰>
```

---

## 배포 확인

- VSCode Marketplace: https://marketplace.visualstudio.com/items?itemName=kimmojae.naps-theme
- Open VSX: https://open-vsx.org/extension/kimmojae/naps-theme

---

## 참고

- VSCode Marketplace: VSCode에서 검색됨
- Open VSX: Cursor, Gitpod 등 VSCode 포크 에디터에서 검색됨
- 검색에 반영되기까지 몇 분 ~ 몇 시간 걸릴 수 있음
