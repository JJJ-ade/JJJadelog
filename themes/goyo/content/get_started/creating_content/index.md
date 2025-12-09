+++
title = "Creating a Content"
description = "Learn how to create a page with Goyo."
weight = 2
+++

Zola creates and manages documents in the `content` subdirectory. Goyo automatically configures the sidebar based on the structure within `content`. Let's create a simple page to get started.

## Page

First, let's create a page. Create a directory `./content/hello_world` and add an `index.md` file with the following content:

**File: `./content/hello_world/index.md`**

```toml
+++
title = "Hello World"
weight = 1

[extra]
+++
```

You can add markdown content below the front matter:

```markdown
+++
title = "Hello World"
weight = 1

[extra]
+++

# Welcome to Hello World

This is your first page content. You can write any markdown here.

- List item 1
- List item 2

## Subsection

Add more content as needed.
```

After creating this file, you can view it at [http://localhost:1111/hello-world](http://localhost:1111/hello-world)

## Section

Next, let's create a section. A section is a page that holds multiple other pages. We'll create a list section with first and second pages.

Create the following directory structure:
```
content/
└── list/
    ├── _index.md
    ├── first/
    │   └── index.md
    └── second/
        └── index.md
```

**File: `./content/list/_index.md`**

```toml
+++
title = "List"
weight = 2
sort_by = "weight"

[extra]
+++
```

**File: `./content/list/first/index.md`**

```toml
+++
title = "First"
weight = 1

[extra]
+++
```

Add some content:

```markdown
# First Page

This is the first page under the list section.
```

**File: `./content/list/second/index.md`**

```toml
+++
title = "Second"
weight = 2

[extra]
+++
```

Add some content:

```markdown
# Second Page

This is the second page under the list section.
```

You can continue to build your structured documentation in this manner.
