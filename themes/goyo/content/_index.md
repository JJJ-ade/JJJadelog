+++
template = "landing.html"
title = "Goyo"

[extra]
version = "v0.1.0"

[extra.hero]
title = "Welcome to Goyo!"
badge = "✨ Minimalist Documentation Theme"
description = "Inspired by the Korean word \"Goyo\" (고요), meaning calm or serene, Goyo is a Zola theme that aims for simplicity and clean documentation. With Goyo, you can easily create beautiful and practical documentation pages."
image = "/images/landing.jpg"
cta_buttons = [
    { text = "Get Started", url = "/introduction", style = "primary" },
    { text = "View on GitHub", url = "https://github.com/hahwul/goyo", style = "secondary" },
]

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

[[extra.features_section.features]]
title = "Customization and Elegant Landing Page"
desc = "Highly customizable with a beautiful landing page."
icon = "fa-solid fa-palette"

[[extra.features_section.features]]
title = "SEO Optimized"
desc = "Provides a structure optimized for search engines."
icon = "fa-solid fa-magnifying-glass-chart"

[[extra.features_section.features]]
title = "Various Shortcodes"
desc = "Offers a variety of useful shortcodes."
icon = "fa-solid fa-code"

[[extra.features_section.features]]
title = "Dark & Light Mode"
desc = "Supports both dark and light modes."
icon = "fa-solid fa-circle-half-stroke"

[extra.trust_section]
title = "Tech Stack"
logos = [
    { src = "/resources/zola.svg", alt = "Zola" },
    { src = "/resources/tailwindcss.svg", alt = "Tailwindcss" },
    { src = "/resources/daisyui.svg", alt = "DaisyUI"},
]

[extra.showcase_section]
title = "Theme Showcase"
subtitle = "Explore different aspects of Goyo theme"

[[extra.showcase_section.tabs]]
name = "Documentation"
title = "Clean Documentation"
description = "Experience beautiful and readable documentation pages with Goyo's minimalist design approach."
image = "/writing/shortcodes/gallery/images/image5.jpeg"

[[extra.showcase_section.tabs]]
name = "Customization"
title = "Easy Customization"
description = "Customize your site with simple configuration options. Change colors, fonts, and layout with ease."
image = "/writing/shortcodes/gallery/images/image1.jpeg"

[[extra.showcase_section.tabs]]
name = "Multilingual"
title = "Multilingual Support"
description = "Built-in support for multiple languages. Create content in different languages and let users switch between them seamlessly."
image = "/writing/shortcodes/gallery/images/image6.jpeg"

[extra.social_proof_section]
title = "What Our Users Say"
testimonials = [
    { author = "KSG", role = "Security Developer / OWASP Noir", quote = "Without extra tools, it includes practical features like search, multilingual support, and comments out of the box", avatar = "/resources/ksg.jpg" },
    { author = "Lina", role = "Security Engineer", quote = "It's so simple and fast, yet I can apply an incredibly beautiful theme, which I absolutely love! I'm ready to embark on a journey to find the calm in my heart with this theme!", avatar = "/resources/lina.jpg" },
    { author = "Bori Bae", role = "Security Engineer", quote = "The theme is clean and the settings are intuitive, so even first-time users can easily use it!", avatar = "/resources/bori.png" },
]

[extra.final_cta_section]
title = "Contributing"
description = "Goyo is an open-source project made with ❤️. If you want to contribute to this project, please see CONTRIBUTING.md and submit a pull request with your cool content!"
button = { text = "View Contributing Guide", url = "/contributing" }
+++
