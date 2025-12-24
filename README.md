# tour_guide.html — 외부 공개(배포) 안내

이 리포지토리의 `tour_guide.html`(베트남 음식 & 여행 가이드 Reveal.js 슬라이드)을 외부(인터넷)에서 바로 열어볼 수 있도록 배포하는 방법과 예상 URL을 정리합니다. 파일을 루트에 커밋하여 푸시합니다.

원본 파일
- tour_guide.html: https://github.com/isis0317/hahaha_home/blob/804b05d409c2e3b2684bbdc0fbbfca8de2a548aa/tour_guide.html

예상 공개 URL
- 파일을 그대로 두었을 때: https://isis0317.github.io/hahaha_home/tour_guide.html
- 파일을 `index.html`로 이름 변경하면: https://isis0317.github.io/hahaha_home/

권장 방법 — GitHub Pages (간단하고 무료)
1. 파일 위치 확인
   - `tour_guide.html`을 리포지토리 루트 또는 `docs/` 폴더에 둡니다.

2. Pages 활성화 (GitHub)
   - 리포지토리 → Settings → Pages
   - Source: 브랜치(예: `main`)와 폴더(`root` 또는 `docs`) 선택 → Save
   - 몇 분 내에 사이트가 배포됩니다.

3. 루트로 바로 열리게 하려면
   - `tour_guide.html`을 `index.html`로 복사하거나 이름 변경
   - 또는 루트에 리디렉트용 `index.html` 추가:
     ```html
     <!doctype html>
     <meta http-equiv="refresh" content="0;url=tour_guide.html">
     ```

대체 배포 옵션
- Netlify: GitHub 연동 후 Publish directory를 `root` 또는 `docs`로 지정
- Vercel: GitHub 연동 후 정적 사이트로 배포
- 임시 외부 공유: 로컬 서버 + ngrok (python -m http.server 8000 → ngrok http 8000)

자동 배포(선택) — GitHub Actions 예시
.github/workflows/deploy.yml 예시:
```yaml
name: Deploy to GitHub Pages
on:
  push:
    branches: [ main ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

주의 및 팁
- HTTPS: Reveal.js와 Google Fonts는 HTTPS CDN을 사용하므로 HTTPS로 배포하세요.
- 파일 경로 확인: 404 발생 시 Pages 설정의 브랜치와 폴더, 파일 경로를 확인하세요.
- 모바일 폰트: pt 단위 폰트가 클 수 있으니 필요 시 media query로 조정하세요.
- 실시간 환율: 계산기는 고정식(VND ÷ 20)입니다. 실시간 환율 연동 권장.

제가 한 작업
- README.md 파일을 리포지토리 루트에 생성하고 main 브랜치에 커밋, 푸시했습니다.
