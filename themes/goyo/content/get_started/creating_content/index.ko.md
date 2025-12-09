+++
title = "콘텐츠 생성하기"
description = "Goyo로 페이지를 만드는 방법을 알아보세요."
weight = 2
+++

Zola는 `content` 하위 디렉토리에서 문서를 생성하고 관리합니다. Goyo는 `content` 내부 구조에 따라서 Sidebar를 자동으로 구성합니다. 그럼 간단한 페이지를 만들어 문서 작업의 시작을 알려봅시다.

## Page

먼저 페이지를 하나 만들어봅니다. `./content/hello_world` 디렉토리를 생성하고 다음 내용으로 `index.md` 파일을 추가합니다:

**파일: `./content/hello_world/index.md`**

```toml
+++
title = "Hello World"
weight = 1

[extra]
+++
```

프론트메터 아래에 마크다운 콘텐츠를 추가할 수 있습니다:

```markdown
+++
title = "Hello World"
weight = 1

[extra]
+++

# Hello World에 오신 것을 환영합니다

이것은 첫 번째 페이지 콘텐츠입니다. 여기에 마크다운을 작성할 수 있습니다.

- 목록 항목 1
- 목록 항목 2

## 하위 섹션

필요에 따라 더 많은 콘텐츠를 추가하세요.
```

이 파일을 생성한 후 [http://localhost:1111/hello-world](http://localhost:1111/hello-world)에서 확인할 수 있습니다.

## Section

이번에는 섹션을 만들어봅니다. 섹션은 여러 페이지를 담고 있는 페이지입니다. list 하위에 first, second 란 페이지를 만들어봅니다.

다음과 같은 디렉토리 구조를 생성합니다:
```
content/
└── list/
    ├── _index.md
    ├── first/
    │   └── index.md
    └── second/
        └── index.md
```

**파일: `./content/list/_index.md`**

```toml
+++
title = "List"
weight = 2
sort_by = "weight"

[extra]
+++
```

**파일: `./content/list/first/index.md`**

```toml
+++
title = "First"
weight = 1

[extra]
+++
```

콘텐츠를 추가합니다:

```markdown
# 첫 번째 페이지

이것은 list 섹션 아래의 첫 번째 페이지입니다.
```

**파일: `./content/list/second/index.md`**

```toml
+++
title = "Second"
weight = 2

[extra]
+++
```

콘텐츠를 추가합니다:

```markdown
# 두 번째 페이지

이것은 list 섹션 아래의 두 번째 페이지입니다.
```

이런 형태로 구조화된 문서를 만들어갈 수 있습니다.
