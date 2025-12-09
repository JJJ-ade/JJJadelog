+++
title = "Creating a Landing Page"
description = "Learn how to create a modern, feature-rich landing page with Goyo."
weight = 3
sort_by = "weight"

[extra]
+++

The landing page is the first page visitors see. In Goyo, it's built using `landing.html` and configured in `content/_index.md`. This allows you to create a rich, engaging entry point for your project.

To create a landing page for another language, simply create a corresponding file, such as `content/_index.ko.md`.

## Template Configuration

First, ensure your `_index.md` file is set to use the `landing.html` template.

```toml
template = "landing.html"
```

## Full Configuration Example

The Goyo landing page is highly customizable through the `[extra]` section of your `_index.md`. Below is a full example showcasing all available sections. You can omit any section you don't need, and it won't be rendered.

```toml
+++
template = "landing.html"
title = "Goyo"

[extra]
version = "v0.1.0"

# Hero Section
# The main section at the top of the page.
[extra.hero]
title = "Welcome to Goyo!"
badge = "✨ Minimalist Documentation Theme"
description = "A simple and clean Zola theme for documentation."
image = "/images/landing.jpg" # Background image
cta_buttons = [
    { text = "Get Started", url = "/get-started/installation/", style = "primary" },
    { text = "View on GitHub", url = "https://github.com/your/repo", style = "secondary" },
]

# Features Section
# A grid to highlight key features.
# Configure the section title and description
[extra.features_section]
title = "Essential Features"
description = "Clean, minimal, and focused on content"

[[extra.features_section.features]]
title = "Documentation Friendly"
desc = "Provides a clean writing experience for documentation."
icon = "fa-solid fa-book"

[[extra.features_section.features]]
title = "Simple Design"
desc = "A theme that pursues minimalism."
icon = "fa-solid fa-minimize"

# Trust Section
# Display logos of companies or projects that trust you.
[extra.trust_section]
title = "Trusted by the Best"
logos = [
    { src = "/images/logo1.svg", alt = "Company One" },
    { src = "/images/logo2.svg", alt = "Company Two" },
]

# Showcase Section
# Display tabbed content with images or text.
# Each tab can show either an image or text content (title + description).
[extra.showcase_section]
title = "Theme Showcase"
subtitle = "Explore different aspects of Goyo theme"

[[extra.showcase_section.tabs]]
name = "Documentation"
title = "Clean Documentation"
description = "Experience beautiful and readable documentation pages with Goyo's minimalist design approach."
image = "/writing/shortcodes/gallery/images/image1.jpeg"

[[extra.showcase_section.tabs]]
name = "Customization"
title = "Easy Customization"
description = "Customize your site with simple configuration options."
image = "/writing/shortcodes/gallery/images/image5.jpeg"

[[extra.showcase_section.tabs]]
name = "Multilingual"
title = "Multilingual Support"
description = "Built-in support for multiple languages."
image = "/writing/shortcodes/gallery/images/image6.jpeg"

# Social Proof Section
# Showcase testimonials from your users.
[extra.social_proof_section]
title = "What Our Users Say"
testimonials = [
    {
        author = "Jane Doe",
        role = "Developer at TechCorp",
        quote = "Goyo has transformed our documentation process. It's simple, elegant, and incredibly fast.",
        avatar = "/images/avatars/jane.png"
    },
    {
        author = "John Smith",
        role = "Project Manager at Innovate LLC",
        quote = "The best Zola theme for documentation out there. The setup was a breeze.",
        avatar = "/images/avatars/john.png"
    },
]

# Final Call to Action Section
# A final prompt for users before the footer.
# You can also add an image field to show an image above the CTA text.
[extra.final_cta_section]
title = "Ready to Get Started?"
description = "Begin your journey with Goyo today and create beautiful documentation with ease."
button = { text = "Start Now", url = "/get-started/installation/" }
image = "/images/contribute.png" # (Optional) Image above the CTA section
+++
```

## Section Breakdown

- **`[extra.hero]`**: The main banner. It includes a title, description, a full-screen background image, and a list of call-to-action buttons (`cta_buttons`). Each button has `text`, `url`, and `style` (`primary` for the main button, `secondary` for the other).

- **`[extra.features_section]`**: Configures the features section title and description. This section is optional - if not provided, defaults to "Essential Features" and "Clean, minimal, and focused on content". Configure with:
  - `title`: The heading text displayed above the features grid
  - `description`: The subtitle text displayed below the title

- **`[[extra.features_section.features]]`**: A list of features to display in a grid, nested under the `features_section`. Each feature has a `title`, `desc` (description), and an `icon` from [Font Awesome](https://fontawesome.com/). For backward compatibility, you can still use `[[extra.features]]` at the top level, but the nested structure is recommended.

- **`[extra.trust_section]`**: Showcases logos of companies or projects. `logos` is a list where each item has an image `src` and `alt` text.

- **`[extra.showcase_section]`**: Displays tabbed content with images or text. The section has a `title` and optional `subtitle`. Each tab in `tabs` array has:
  - `name`: The tab label displayed in the navigation
  - `title`: Content title (shown when no image is provided)
  - `description`: Content description (shown when no image is provided)
  - `image`: (Optional) Image path. When provided, only the image is displayed. When omitted, the title and description are shown instead.
  Images are displayed with a fixed width of 1024px for consistent presentation.

- **`[extra.social_proof_section]`**: Displays user testimonials. `testimonials` is a list of objects, each with an `author`, `role`, `quote`, and `avatar` image.

- **`[extra.final_cta_section]`**: A final call-to-action block with a `title`, `description`, and a single `button` with `text` and `url`.
  You can also add an optional `image` field (e.g. `image = "/images/contribute.png"`) to display an image above the CTA text.
