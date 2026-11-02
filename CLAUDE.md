# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

개인 포트폴리오 정적 사이트입니다. 실제 사이트는 `index.html` 한 파일이 전부이며, HTML, CSS, JS가 모두 이 파일 안에 있습니다.

로컬 폴더 이름은 `claude-play`이지만 원격 저장소는 `nar992024/my-profile-site`입니다.

## 기술 스택

- HTML + 순수 JavaScript (프레임워크 없음)
- Tailwind CSS: CDN(`cdn.tailwindcss.com`)에서 불러와 브라우저에서 실행
- Google Fonts(Inter), DiceBear 아바타 이미지

이 외부 리소스를 모두 네트워크에서 불러오므로 오프라인에서는 화면이 제대로 표시되지 않습니다.

## 빌드 & 실행 명령어

현재는 빌드, 린트, 테스트 도구와 `package.json`이 없습니다. `.claude/CLAUDE.md`의 `npm` 명령은 React 전환 후에 쓸 수 있으며, 지금은 설치 없이 파일을 브라우저로 열어 확인합니다.

```powershell
# 로컬에서 화면 확인 (Windows)
Start-Process .\index.html
```

공개 사이트: https://nar992024.github.io/my-profile-site/

수정 내용은 원격에 push한 뒤 Pages 배포가 끝나야 공개 사이트에 반영됩니다.

## 코드 컨벤션

공통 규칙은 `.claude/rules/code-style.md`를 따릅니다. `index.html`의 기존 코드에는 다음 관례가 있습니다.

- **스타일:** Tailwind 유틸리티 클래스를 먼저 쓰고, 표현하기 어려운 효과만 `<style>` 블록에 kebab-case 클래스(`.glow-card`, `.card-hover`)로 추가합니다.
- **색상:** 커스텀 색상(`dark`, `darker`, `card`, `lime`, `limeLight`)을 사용합니다.
- **요소 ID:** JS에서 참조하는 ID는 camelCase(`menuBtn`, `typingText`)입니다.

## 프로젝트 구조

`index.html`은 위에서부터 다음 순서로 구성됩니다.

- `<head>`: 인라인 `tailwind.config`(커스텀 색상, 글꼴)와 `<style>` 블록
- `<body>`: 헤더, 히어로, `#about`, `#skills`, `#projects`, `#contact`, 푸터
- `</body>` 앞 인라인 `<script>`: 모바일 메뉴 토글과 히어로 타이핑 애니메이션 (문구는 `roles` 배열에서 수정)

`login.md`와 `test1~4.txt`는 한 줄짜리 파일로 `index.html`에서 사용하지 않습니다. `login.md`에는 로그인 기능을 구현했다고 적혀 있지만 이 저장소에 로그인 코드는 없습니다.

## 예정된 구조 (아직 없음)

이 저장소를 React 할일 관리 앱으로 전환할 계획입니다. 아래 내용은 아직 구현되지 않았으므로, 전환 작업을 요청받기 전에는 위의 현재 구조를 기준으로 작업합니다. 전환 후에는 이 내용을 위 섹션들에 반영합니다.

- **기술 스택:** React 19 + TypeScript, Tailwind CSS, Zustand(상태관리)
- **명령어:** 개발 서버 `npm run dev`, 빌드 `npm run build`, 테스트 `npm run test`
- **파일명:** 컴포넌트는 PascalCase(`TodoList.tsx`), 훅은 `use`로 시작(`useTodos.ts`)
- **구조:** `src/components/`(UI 컴포넌트), `src/hooks/`(커스텀 훅), `src/types/`(타입 정의), `src/stores/`(Zustand 스토어)

## 수정 시 주의할 점

- **내비게이션 메뉴는 두 곳에 있습니다.** 데스크톱 메뉴와 `#mobileMenu`가 따로 작성되어 있어 항목을 바꾸면 양쪽을 함께 수정해야 합니다.
- **색상 값이 중복되어 있습니다.** 라임색 `#CEFD3D`는 `tailwind.config`와 `<style>` 블록에 각각 적혀 있습니다(`rgba(206, 253, 61, …)` 형태 포함). 색상을 바꾸면 모두 수정해야 합니다.
- **아직 채워지지 않은 내용이 있습니다.** 프로젝트 카드(`Project 1~3`)의 이름과 `View Details` 링크, 소셜 링크는 `href="#"`인 임시 값입니다.
