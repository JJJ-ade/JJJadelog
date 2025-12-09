+++
title = "기여하기"
description = "Goyo에 기여하는 방법"
weight = 7
sort_by = "weight"

[extra]
+++

Goyo에 관심을 가져주셔서 감사합니다! 우리는 모든 분들의 기여를 환영하며 Goyo를 더 좋게 만드는 데 도움을 주셔서 감사드립니다.

## 기여 방법

Goyo에 기여할 수 있는 여러 가지 방법이 있습니다:

- **버그 리포트**: 버그를 발견하셨나요? GitHub에 [이슈를 열어](https://github.com/hahwul/goyo/issues/new) 문제에 대한 세부 사항을 알려주세요.
- **기능 제안**: 새로운 기능에 대한 아이디어가 있으신가요? 듣고 싶습니다! 제안을 논의하기 위해 이슈를 열어주세요.
- **문서 개선**: 문서를 더 명확하고 포괄적으로 만드는 데 도움을 주세요.
- **코드 제출**: 버그를 수정하고, 기능을 추가하거나, 풀 리퀘스트를 제출하여 기존 코드를 개선하세요.
- **경험 공유**: 블로그 포스트를 작성하고, 튜토리얼을 만들거나, Goyo로 만든 사이트를 커뮤니티와 공유하세요.

## 시작하기

### 사전 요구사항

기여를 시작하기 전에 다음 항목이 설치되어 있는지 확인하세요:

- **Zola**: v0.21.0 이상 ([설치 가이드](https://www.getzola.org/documentation/getting-started/installation/))
- **Just**: 빌드 자동화를 위한 작업 실행기 ([설치 가이드](https://github.com/casey/just))
- **Git**: 버전 관리용

### 개발 환경 설정

1. **저장소 포크**: [Goyo GitHub 저장소](https://github.com/hahwul/goyo)에서 "Fork" 버튼을 클릭하세요.

2. **포크 클론**:
   ```bash
   git clone https://github.com/YOUR-USERNAME/goyo.git
   cd goyo
   ```

3. **의존성 설정**:
   ```bash
   # TailwindCSS와 DaisyUI 설치
   cd /tmp
   curl -sLo tailwindcss https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-linux-x64
   chmod +x tailwindcss
   mv tailwindcss ../goyo/src/
   
   cd ../goyo
   curl -sLo src/daisyui.js https://github.com/saadeghi/daisyui/releases/latest/download/daisyui.js
   curl -sLo src/daisyui-theme.js https://github.com/saadeghi/daisyui/releases/latest/download/daisyui-theme.js
   ```

4. **사이트 빌드**:
   ```bash
   just build
   ```

5. **개발 서버 시작**:
   ```bash
   just dev
   ```
   
   사이트는 `http://127.0.0.1:1111`에서 확인할 수 있습니다.

## 변경 사항 작성

### 코드 가이드라인

- **기존 패턴 따르기**: 기존 코드와 문서를 살펴보고 프로젝트의 스타일과 구조를 이해하세요.
- **간단하게 유지**: 복잡한 해결책보다 간단하고 명확한 해결책을 선호하세요.
- **변경 사항 테스트**: 제출하기 전에 로컬에서 변경 사항을 빌드하고 테스트하세요.
- **명확한 커밋 메시지 작성**: 무엇을, 왜 설명하는 설명적인 커밋 메시지를 사용하세요.

### 문서 가이드라인

- **명확한 언어 사용**: 간단하고 이해하기 쉬운 언어로 작성하세요.
- **예제 제공**: 도움이 되는 경우 코드 예제와 스크린샷을 포함하세요.
- **구조 따르기**: 기존 문서 페이지와 동일한 구조와 형식을 사용하세요.
- **다국어 지원**: 가능하다면 번역을 제공하세요(특히 한국어).

### 템플릿 및 테마 변경

- **철저한 테스트**: 테마 변경은 많은 페이지에 영향을 줄 수 있으므로 광범위하게 테스트하세요.
- **반응성 고려**: 변경 사항이 다양한 화면 크기에서 잘 작동하는지 확인하세요.
- **접근성 유지**: 모든 사용자가 테마에 접근할 수 있도록 유지하세요.
- **다크/라이트 모드 확인**: 두 가지 색상 구성표에서 변경 사항이 작동하는지 확인하세요.

## 풀 리퀘스트 제출

1. **브랜치 생성**: 변경 사항을 위한 새 브랜치를 만드세요:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **변경 사항 작성**: 위의 가이드라인을 따라 변경 사항을 구현하세요.

3. **로컬 테스트**: 변경 사항을 빌드하고 테스트하세요:
   ```bash
   just build
   zola check --skip-external-links
   just dev
   ```

4. **변경 사항 커밋**:
   ```bash
   git add .
   git commit -m "기능 추가: 기능 설명"
   ```

5. **포크에 푸시**:
   ```bash
   git push origin feature/your-feature-name
   ```

6. **풀 리퀘스트 열기**: [Goyo 저장소](https://github.com/hahwul/goyo)로 이동하여 "New Pull Request"를 클릭하세요. 변경 사항과 필요한 이유에 대한 명확한 설명을 제공하세요.

## 풀 리퀘스트 가이드라인

- **PR당 하나의 기능**: 풀 리퀘스트를 단일 기능 또는 수정에 집중하세요.
- **변경 사항 설명**: PR이 수행하는 작업과 필요한 이유를 설명하세요.
- **이슈 참조**: PR이 이슈를 해결하는 경우 참조하세요(예: "Fixes #123").
- **인내심 갖기**: 관리자가 가능한 한 빨리 PR을 검토할 것입니다.
- **피드백에 열린 자세**: 리뷰 피드백을 기반으로 변경할 준비를 하세요.

## 개발 팁

### 프로젝트 구조

```
goyo/
├── content/          # 문서 및 콘텐츠
├── static/           # 정적 자산(이미지, 폰트 등)
├── templates/        # Zola HTML 템플릿
├── src/              # 소스 파일(CSS, JS 도구)
├── config.toml       # 사이트 구성
└── theme.toml        # 테마 메타데이터
```

### 일반적인 작업

```bash
# 사이트 빌드
just build

# 개발 서버 시작
just dev

# 내부 링크 확인
zola check --skip-external-links

# 빌드 디렉토리 정리
rm -rf public
```

### 변경 사항 테스트

제출하기 전에 항상 변경 사항을 테스트하세요:

1. **빌드 테스트**: 사이트가 오류 없이 빌드되는지 확인
2. **링크 확인**: 모든 내부 링크가 작동하는지 확인
3. **시각적 테스트**: 브라우저에서 사이트 확인
4. **다국어 테스트**: 영어 및 한국어 버전 모두 테스트(해당되는 경우)
5. **테마 테스트**: 다크 및 라이트 모드 모두 확인

## 행동 강령

우리는 모든 사람에게 환영하고 포용적인 환경을 제공하기 위해 노력합니다. 다음을 준수해 주세요:

- 존중하고 배려하세요
- 신규 참여자를 환영하고 시작하는 데 도움을 주세요
- 커뮤니티에 가장 좋은 것에 집중하세요
- 다른 커뮤니티 구성원에게 공감을 보여주세요

## 도움 받기

도움이 필요하거나 질문이 있는 경우:

- **GitHub 이슈**: [이슈를 열어](https://github.com/hahwul/goyo/issues) 질문하세요
- **GitHub 토론**: 기능 및 개선 사항에 대한 토론에 참여하세요
- **문서**: 가이드 및 참고 자료는 [Goyo 문서](https://goyo.hahwul.com)를 확인하세요

## 인정

기여자는 다음에서 인정받습니다:

- 프로젝트의 커밋 히스토리
- 중요한 기여에 대한 릴리스 노트
- GitHub 기여자 페이지

Goyo에 기여해 주셔서 감사합니다! 여러분의 노력이 이 프로젝트를 모두를 위해 더 좋게 만듭니다. ❤️
