# 🚀 우주 탐사 퀴즈 (Space Quiz)

우주에 대한 흥미로운 10개의 질문으로 당신의 우주 지식을 테스트하세요! 이 앱은 의존성 없는 단일 HTML 파일로 만들어졌으며, 즉시 브라우저에서 실행할 수 있습니다.

## ✨ 주요 기능

- 🌟 **10개의 우주 탐사 퀴즈** - 흥미로운 한국어 질문들
- 📊 **실시간 진행 추적** - 진행률 바, 정답/오답 카운터, 정확도 표시
- 🎨 **생생한 피드백** - 정답은 녹색 펄스, 오답은 빨간색 흔들림 애니메이션
- 🎭 **이모지 결과 화면** - 점수에 따라 다른 이모지 반응 (🌟 🚀 👍 🤔 😢)
- 🌓 **다크/라이트 모드** - `prefers-color-scheme` 지원으로 자동 테마 전환
- ⌨️ **키보드 네비게이션** - Tab과 Enter 키로 완전한 접근성 지원
- 🎮 **미션 컨트롤 UI** - 선택된 요소가 스캔라인 효과와 "LOCKED" 표시기를 보여줍니다

## 🚀 빠른 시작

### 온라인 플레이
GitHub Pages에서 직접 플레이하세요:
```
https://yh1209.github.io/space-quiz/
```

### 로컬 실행
1. 저장소를 클론하세요:
```bash
git clone https://github.com/yh1209/space-quiz.git
cd space-quiz
```

2. `index.html`을 브라우저에서 열면 됩니다:
```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

또는 간단히 파일을 더블클릭하여 열어도 됩니다.

## 📁 프로젝트 구조

```
space-quiz/
├── index.html                 # 전체 앱 (HTML + CSS + JavaScript)
├── README.md                  # 이 파일
└── .github/
    ├── copilot-instructions.md  # Copilot을 위한 개발 가이드
    └── workflows/
        └── deploy.yml         # GitHub Pages 배포 워크플로
```

## 🛠️ 개발 가이드

### 질문 추가하기
`index.html`의 `questions` 배열에 새 질문을 추가하세요:

```javascript
{
  question: "질문 텍스트",
  options: ["선택지1", "선택지2", "선택지3", "선택지4"],
  correct: 1  // 정답의 인덱스 (0-3)
}
```

### 스타일 커스터마이징
CSS 변수를 편집하여 색상을 변경하세요:

```css
:root {
  --primary: #6366f1;    /* 주요 색상 */
  --success: #10b981;    /* 정답 색상 */
  --error: #ef4444;      /* 오답 색상 */
}
```

더 자세한 개발 가이드는 `.github/copilot-instructions.md`를 참고하세요.

## 🌐 배포

이 리포지토리는 GitHub Pages와 자동 배포를 지원합니다:

1. GitHub Actions 워크플로가 master 브랜치에 푸시될 때마다 자동으로 실행됩니다
2. 정적 파일이 `gh-pages` 브랜치로 배포됩니다
3. GitHub Pages 설정에서 `gh-pages` 브랜치를 소스로 사용하도록 설정됩니다

배포된 사이트: https://yh1209.github.io/space-quiz/

## 🎯 테스트

브라우저에서 수동으로 테스트하세요:

- ✅ 정답을 선택했을 때 "✓ 정답입니다!" 메시지와 초록색 피드백
- ✅ 오답을 선택했을 때 "❌ 틀렸어요" 메시지와 빨간색 피드백
- ✅ 점수와 정확도가 실시간으로 업데이트
- ✅ 진행 바가 순조롭게 움직임
- ✅ 모든 10개 질문을 완료하면 결과 화면이 표시됨
- ✅ Tab 키로 선택지 사이를 이동하고 Enter 키로 선택 가능
- ✅ 시스템 다크 모드를 켜고 꺼서 테마가 자동으로 전환되는지 확인

## 📱 브라우저 호환성

- ✅ Chrome/Chromium
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ✅ 모바일 브라우저 (iOS Safari, Chrome Mobile 등)

## 🚀 향후 개선 사항

- [ ] 난이도 선택 (쉬움/중간/어려움)
- [ ] 점수를 localStorage에 저장하여 기록 추적
- [ ] 각 문제마다 시간 제한
- [ ] 질문과 답변 순서 무작위 섞기
- [ ] 결과를 JSON으로 내보내기

## 📄 라이선스

이 프로젝트는 자유롭게 사용할 수 있습니다.

## 👨‍💻 기여

개선 사항이나 버그 보고는 이슈를 열거나 풀 리퀘스트를 제출해주세요!

---

**만든 사람**: Copilot with ❤️
