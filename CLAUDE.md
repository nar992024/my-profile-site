# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

개인 포트폴리오 정적 사이트입니다. 실제 사이트는 `index.html` 한 파일이 전부이며, HTML, CSS, JS가 모두 이 파일 안에 있습니다.

로컬 폴더 이름은 `claude-play`이지만 원격 저장소는 `nar992024/my-profile-site`입니다.

## 명령어

빌드, 린트, 테스트 도구와 `package.json`이 없습니다. 설치 없이 파일을 브라우저로 열어 확인합니다.

```powershell
# 로컬에서 화면 확인 (Windows)
Start-Process .\index.html
```

공개 사이트: https://nar992024.github.io/my-profile-site/

수정 내용은 원격에 push한 뒤 Pages 배포가 끝나야 공개 사이트에 반영됩니다.

## 구조

- **스타일:** Tailwind를 CDN(`cdn.tailwindcss.com`)에서 불러와 브라우저에서 실행합니다. 커스텀 색상(`dark`, `darker`, `card`, `lime`, `limeLight`)과 글꼴은 `<head>`의 인라인 `tailwind.config`에 정의되어 있습니다. Tailwind로 표현하기 어려운 효과(`.glow-card`, `.card-hover`, `.italic-lime` 등)는 그 아래 `<style>` 블록에 있습니다.
- **스크립트:** `</body>` 앞의 인라인 `<script>` 하나에 모바일 메뉴 토글과 히어로 영역의 타이핑 애니메이션이 있습니다. 타이핑 문구는 `roles` 배열에서 수정합니다.
- **외부 의존성:** Tailwind, Google Fonts(Inter), DiceBear 아바타 이미지를 모두 네트워크에서 불러오므로 오프라인에서는 화면이 제대로 표시되지 않습니다.

## 수정 시 주의할 점

- **내비게이션 메뉴는 두 곳에 있습니다.** 데스크톱 메뉴와 `#mobileMenu`가 따로 작성되어 있어 항목을 바꾸면 양쪽을 함께 수정해야 합니다. 링크는 각 섹션의 `id`(`about`, `skills`, `projects`, `contact`)를 가리킵니다.
- **색상 값이 중복되어 있습니다.** 라임색 `#CEFD3D`는 `tailwind.config`와 `<style>` 블록에 각각 적혀 있습니다(`rgba(206, 253, 61, …)` 형태 포함). 색상을 바꾸면 모두 수정해야 합니다.
- **아직 채워지지 않은 내용이 있습니다.** 프로젝트 카드(`Project 1~3`)의 이름과 `View Details` 링크, 소셜 링크는 `href="#"`인 임시 값입니다.

## 사이트와 무관한 파일

`login.md`와 `test1~4.txt`는 한 줄짜리 파일로 `index.html`에서 사용하지 않습니다. `login.md`에는 로그인 기능을 구현했다고 적혀 있지만 이 저장소에 로그인 코드는 없습니다.
