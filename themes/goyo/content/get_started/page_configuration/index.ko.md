+++
title = "페이지 설정"
description = "Goyo에서 개별 페이지를 설정하는 방법을 배웁니다."
weight = 5
sort_by = "weight"

[extra]
toc_expand = true
badge = "NEW"
+++

페이지 설정을 사용하면 Goyo 문서 사이트의 개별 페이지 동작과 모양을 사용자 정의할 수 있습니다. 이러한 설정은 각 콘텐츠 파일의 front matter에서 `[extra]` 섹션을 사용하여 정의됩니다.

> **참고:** 이 페이지는 `toc_expand`와 `badge` 기능을 모두 보여줍니다 - 오른쪽의 목차가 기본적으로 완전히 펼쳐져 있고, 페이지 제목 옆에 "NEW" 배지가 있는 것을 확인하세요!

## 배지 표시

페이지나 섹션에 배지 표시를 추가하려면 `[extra]` 섹션에 `badge` 필드를 포함하면 됩니다:

```toml
+++
title = "페이지 제목"
description = "페이지 설명"

[extra]
badge = "NEW"
+++
```

배지는 페이지 제목 오른쪽에 스타일이 지정된 표시로 나타납니다. 다음과 같은 내용을 강조하는 데 유용합니다:
- 새로운 콘텐츠
- 베타 기능
- 업데이트된 페이지
- 중요한 공지사항

일반적인 배지 값:
- `NEW` - 새로 추가된 콘텐츠
- `BETA` - 베타 단계의 기능
- `UPDATED` - 최근 업데이트된 콘텐츠
- `WIP` - 작업 중인 콘텐츠

`badge` 필드를 설정하지 않으면 배지가 표시되지 않습니다.

## 목차(TOC) 설정

### TOC 펼치기
`toc_expand`

- `toc_expand`: 페이지의 목차(TOC)가 기본적으로 펼쳐질지 여부를 제어합니다.
  - `false` (기본값): TOC 섹션이 접혀있으며 스크롤 위치에 따라 자동으로 펼쳐지거나 접힙니다
  - `true`: TOC 섹션이 기본적으로 펼쳐져 있으며 스크롤 위치와 관계없이 펼쳐진 상태로 유지됩니다

**기본 동작 (toc_expand = false 또는 설정하지 않음):**
```toml
+++
title = "내 페이지"
description = "페이지 설명"

[extra]
# TOC는 기본적으로 접혀있고 스크롤에 따라 자동으로 펼쳐집니다
+++
```

`toc_expand`가 설정되지 않았거나 `false`로 설정된 경우, TOC는 동적으로 동작합니다:
- 하위 제목이 있는 섹션은 기본적으로 접혀있습니다
- 스크롤하면 현재 섹션이 자동으로 펼쳐집니다
- 다른 섹션은 깔끔한 보기를 유지하기 위해 접힙니다

**펼쳐진 TOC (toc_expand = true):**
```toml
+++
title = "내 페이지"
description = "페이지 설명"

[extra]
toc_expand = true
+++
```

`toc_expand`가 `true`로 설정된 경우:
- 모든 TOC 섹션이 기본적으로 펼쳐집니다
- 모든 섹션은 스크롤 위치와 관계없이 펼쳐진 상태로 유지됩니다
- 여러 짧은 섹션이 있는 페이지에서 모든 제목을 한 번에 보고 싶을 때 유용합니다

## 사용 예제

다음은 펼쳐진 TOC를 사용하는 페이지의 전체 예제입니다:

```toml
+++
title = "API 참조"
description = "모든 엔드포인트가 표시된 전체 API 문서"
weight = 10

[extra]
toc_expand = true
+++

# API 참조

이 페이지는 TOC가 완전히 펼쳐진 상태로 모든 API 엔드포인트를 보여줍니다.

## 인증
인증에 대한 세부 정보...

## 엔드포인트
### GET /api/users
### POST /api/users
### DELETE /api/users

## 오류 코드
### 400 Bad Request
### 401 Unauthorized
### 404 Not Found
```

`toc_expand = true`를 사용하면 독자가 TOC에서 모든 엔드포인트와 오류 코드를 한 번에 볼 수 있어 API 참조를 쉽게 탐색할 수 있습니다.
