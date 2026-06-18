# Notebook

A dotted-paper, notebook-feel Hugo theme for blogs. Built from scratch with no
external font or JS dependencies — just one stylesheet and a tiny inline script
for the dark-mode toggle.

Notebook screenshot

## Features

- **Dotted-paper background** across the whole page
- **Margin spine navigation** — a sticky vertical nav along a colored margin line
- **Highlighter accents** — links and titles fill with a marker swipe on hover; nav
and tags use a sweeping underline
- **Dark mode** with a toggle, persisted in `localStorage` and applied before paint
(no flash). Honors a configurable default theme.
- **Post cards** with summaries, reading time, tags, and a turned-up page corner
- **System font stack** (matches the OS UI) — no web fonts to download
- Responsive; the spine nav collapses to a top bar on small screens

## Requirements

Hugo **extended** `0.146.0` or newer (the stylesheet is processed with Hugo Pipes:
`resources.Get | minify | fingerprint`).

## Installation

### As a Hugo Module (recommended)

```sh
hugo mod init github.com/you/your-site
```

```toml
# hugo.toml
[module]
  [[module.imports]]
    path = "github.com/its-ammu/hugo-notebook"
```

```sh
hugo mod get -u
```

### As a Git submodule

```sh
git submodule add https://github.com/its-ammu/hugo-notebook.git themes/notebook
```

Then set the theme in your site config:

```toml
theme = "notebook"
```

## Configuration

A minimal `hugo.toml`:

```toml
baseURL = "https://example.com/"
languageCode = "en"
title = "My Notebook"
theme = "notebook"

[params]
  description = "Notes on whatever I'm building."
  author = "Your Name"
  defaultTheme = "light"   # "light" or "dark"
  ShowReadingTime = true
  DateFormat = "January 2, 2006"
  favicon = "favicon.ico"

  # Shown on the home intro card
  [params.profileMode]
    subtitle = "Engineer & writer"

  # Social buttons on the home intro card (icon-only: github, linkedin)
  [[params.socialIcons]]
    name = "github"
    url = "https://github.com/your-handle"
  [[params.socialIcons]]
    name = "linkedin"
    url = "https://www.linkedin.com/in/your-handle/"

# Spine navigation. Mark external links with params.external = true.
[[menu.main]]
  identifier = "posts"
  name = "Posts"
  url = "/posts/"
  weight = 15
[[menu.main]]
  identifier = "tags"
  name = "Tags"
  url = "/tags/"
  weight = 20

[markup.goldmark.renderer]
  unsafe = true   # allow inline SVG/HTML illustrations in posts
```

### Customizing colors

All colors are CSS variables at the top of `assets/css/notebook.css` (light theme in
`:root`, dark theme in `:root[data-theme="dark"]`). The key knobs:

- `--accent` / `--hl` / `--hl-strong` — highlighter color
- `--margin` — the spine / margin line
- `--paper`, `--ink`, `--card` — surfaces and text
- `--rule` (vertical rhythm) and `--dot` (dot-grid spacing)

## Writing posts

Posts live under `content/posts/`. Front matter:

```toml
---
title = "My first post"
date = 2026-01-01
tags = ["hugo", "notebook"]
---
```

Tags and reading time appear automatically on cards and the post header.

## License

[MIT](LICENSE) © Amuthavarsni Rajkumar