+++
title = "Configuration"
description = "Goyo의 설정 방법을 알아보세요."
weight = 4
sort_by = "weight"

[extra]
toc_expand = true
+++

이제 Goyo 테마의 설정을 알아봅니다. 테마를 커스텀하게 사용하기 위한 여러가지 설정을 제공합니다. `config.toml`에서 사용할 수 있습니다.

## 디자인 & 브랜딩

### 로고
`logo_text` / `logo_image_path` / `logo_image_padding`

- `logo_text`: 로고 이미지 없을 때 표시되는 텍스트
- `logo_image_path`: 로고 이미지 경로
- `logo_image_padding`: 로고 이미지에 적용할 padding 값 (예: "5px")

```toml
[extra]
logo_text = "Goyo"
logo_image_path = "images/goyo.png"
logo_image_padding = "5px"
```

### 푸터
`footer_html`

- `footer_html`: 푸터에 표시되는 HTML 코드

```toml
[extra]
footer_html = "Powered by <a href='https://www.getzola.org'>Zola</a> and <a href='https://github.com/hahwul/goyo'>Goyo</a>"
```

푸터는 다음을 표시합니다:
1. 로고 및 사이트 이름
2. Powered by 텍스트 (`footer_html`로 커스터마이징 가능)

## SEO & 소셜

### 썸네일
`default_thumbnail`

- `default_thumbnail`: 기본 썸네일 이미지 경로

```toml
[extra]
default_thumbnail = "images/default_thumbnail.jpg"
```

### 트위터
`twitter_site` / `twitter_creator`

- `twitter_site`: 트위터 사이트 핸들
- `twitter_creator`: 트위터 생성자 핸들

```toml
[extra]
twitter_site = "@hahwul"
twitter_creator = "@hahwul"
```

### 구글 태그
`gtag`

- `gtag`: 구글 태그 ID

```toml
[extra]
gtag = "G-XXXXXXXXXX"
```

## 네비게이션 & UI

### 컬러셋
`default_colorset`

- `default_colorset`: 기본 테마 (dark/light)

```toml
[extra]
default_colorset = "dark"
```

### 폰트
`custom_font_enabled` / `custom_font_name` / `custom_font_path`

- `custom_font_enabled`: 커스텀 폰트 사용 여부. 기본 폰트 대신 사용자 정의 폰트를 사용하려면 `true`로 설정합니다.
- `custom_font_name`: 사용할 폰트 패밀리 이름 (예: `"Roboto"`, `"Noto Sans KR"`).
- `custom_font_path`: 폰트 파일 경로. 다음 두 가지 형식을 지원합니다:
  - **로컬 경로**: `static` 디렉토리 내 로컬 폰트 파일의 상대 경로 (예: `"fonts/custom.woff"`)
  - **원격 URL**: 웹 폰트의 전체 URL (예: `"https://fonts.googleapis.com/css2?family=Roboto"`)

**기본값**: Goyo는 기본적으로 **Pretendard** 폰트를 사용합니다. Pretendard는 한국어와 영어 텍스트에 대해 우수한 가독성을 제공합니다.

**예제 - 로컬 폰트:**
```toml
[extra]
custom_font_enabled = true
custom_font_name = "MyCustomFont"
custom_font_path = "fonts/mycustomfont.woff"
```

**예제 - 구글 폰트:**
```toml
[extra]
custom_font_enabled = true
custom_font_name = "Roboto"
custom_font_path = "https://fonts.googleapis.com/css2?family=Roboto&display=swap"
```

**예제 - 기본값 (Pretendard):**
```toml
[extra]
custom_font_enabled = false  # 기본적으로 Pretendard 폰트 사용
```

### 밝기
`brightness`

- `brightness`: 테마 전반적인 색상의 밝기를 조절합니다. 옵션:
  - `"darker"`: 색상을 더 어둡게 - 다크 테마는 완전히 검정색으로, 라이트 테마는 더 어두운 색으로 변경됩니다
  - `"normal"`: 기본 밝기 (기본값)
  - `"lighter"`: 색상을 더 밝게 - 두 테마 모두 더 밝아집니다

```toml
[extra]
brightness = "normal"  # 옵션: "darker", "normal", "lighter"
```

예시:
- 완전히 검정색인 다크 테마를 원하는 경우: `brightness = "darker"`
- 라이트 테마를 더 어둡게 만들려면: `brightness = "darker"` 와 `default_colorset = "light"` 설정
- 다크 테마를 더 밝게 만들려면: `brightness = "lighter"`

### 사이드바 확장 깊이
`sidebar_expand_depth`

- `sidebar_expand_depth`: 사이드바 섹션이 기본적으로 확장되어야 하는 깊이(최대 5)를 지정합니다. 예를 들어, `1` 값은 최상위 섹션만 표시하고, `2`는 첫 번째 하위 섹션 수준을 확장합니다.

```toml
[extra]
sidebar_expand_depth = 2
```

### 네비게이션
`nav` / `nav_{lang}`

- `nav`: 상단 네비게이션 메뉴입니다. name과 icon 필드는 optional 입니다.
- `nav_{lang}`: 언어별 네비게이션 메뉴입니다 (예: `nav_ko`는 한국어용). 정의되면 해당 언어에서 기본 `nav` 대신 사용됩니다.

```toml
[extra]
# 기본 네비게이션 (영어 및 폴백용)
nav = [
    { name = "Documents", url = "/introduction", type = "url", icon = "fa-solid fa-book" },
    { name = "GitHub", url = "https://github.com/hahwul/goyo", type = "url", icon = "fa-brands fa-github" },
    { name = "Links", type = "dropdown", icon = "fa-solid fa-link", members = [
        { name = "Creator Blog", url = "https://www.hahwul.com", type = "url", icon = "fa-solid fa-fire-flame-curved" },
    ] },
]

# 한국어 네비게이션 (선택사항)
nav_ko = [
    { name = "문서", url = "/ko/introduction", type = "url", icon = "fa-solid fa-book" },
    { name = "GitHub", url = "https://github.com/hahwul/goyo", type = "url", icon = "fa-brands fa-github" },
    { name = "링크", type = "dropdown", icon = "fa-solid fa-link", members = [
        { name = "제작자 블로그", url = "https://www.hahwul.com", type = "url", icon = "fa-solid fa-fire-flame-curved" },
    ] },
]
```

### 언어 별칭
`lang_aliases`

- `lang_aliases`: 언어 선택 드롭다운에 표시될 언어의 사용자 정의 이름입니다. 정의하지 않으면 언어 코드가 표시됩니다. 이를 통해 "en" 또는 "ko" 대신 "English" 또는 "한국어"와 같은 사용자 친화적인 이름을 표시할 수 있습니다.

```toml
[extra]
# 언어 선택기의 언어 표시 이름
lang_aliases = { en = "English", ko = "한국어" }
```

필요한 만큼 언어를 추가할 수 있습니다:

```toml
[extra]
lang_aliases = { 
    en = "English", 
    ko = "한국어",
    ja = "日本語",
    id = "Bahasa Indonesia"
}
```

### 테마 토글 비활성화
`disable_theme_toggle`

- `disable_theme_toggle`: `true`로 설정하면 상단 네비게이션에서 테마(다크/라이트) 토글 버튼이 표시되지 않습니다.

```toml
[extra]
disable_theme_toggle = true
```

### 루트 사이드바 숨기기 비활성화
`disable_root_sidebar_hide`

- `disable_root_sidebar_hide`: `true`로 설정하면 루트 페이지 (`/` 또는 `/{lang}/`)에서 사이드바가 숨겨지지 않습니다. 이를 통해 메인 랜딩 페이지에서도 사이드바를 항상 볼 수 있습니다.

```toml
[extra]
disable_root_sidebar_hide = false
```

{{ image_diff(
    src1="/images/side-home.jpg",
    src2="/images/wide-home.jpg",
    alt="goyo"
) }}

## 콘텐츠 & 공유

### 편집 URL
`edit_url`

- `edit_url`: 페이지 편집을 위한 기본 URL. 설정하면 각 페이지/섹션 하단에 "Edit this page" 링크가 나타나며, 저장소의 소스 파일로 연결됩니다.

```toml
[extra]
edit_url = "https://github.com/hahwul/goyo/edit/main"
```

링크는 자동으로 콘텐츠 파일의 상대 경로를 추가합니다 (예: `content/introduction/_index.md`).

### 공유 버튼
`enable_copy_url` / `enable_share_x`

- `enable_copy_url`: 각 페이지/섹션 하단에 "Copy URL" 버튼을 표시합니다. 클릭하면 현재 페이지 URL을 클립보드에 복사하고 2초간 "Copied!" 확인 메시지를 표시합니다.
- `enable_share_x`: 각 페이지/섹션 하단에 "Share on X" 버튼을 표시합니다. 클릭하면 페이지 URL과 제목이 미리 입력된 트위터 공유 대화상자가 열립니다.

```toml
[extra]
enable_copy_url = false  # 기본값은 false
enable_share_x = false   # 기본값은 false
```

개별적으로 활성화하거나 둘 다 활성화할 수 있습니다:

```toml
[extra]
enable_copy_url = true   # Copy URL 버튼만 활성화
enable_share_x = false   # Share on X는 비활성화 유지
```

```toml
[extra]
enable_copy_url = true   # 두 버튼 모두 활성화
enable_share_x = true
```

### 댓글
`comments`

- `comments`: 댓글 기능 설정 (giscus/utterances)

```toml
[extra.comments]
enabled = true
system = "giscus"
repo = "hahwul/goyo"
repo_id = "R_kgDOPHnqwg"
category = "General"
category_id = "DIC_kwDOPHnqws4CspmC"
mapping = "pathname"
strict = "0"
reactions_enabled = "1"
emit_metadata = "0"
input_position = "bottom"
theme = "catppuccin_mocha"
lang = "en"
```
