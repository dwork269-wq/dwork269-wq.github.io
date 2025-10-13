# Miruvor Blog

A minimalist, fast, and lightweight blog built with Jekyll and GitHub Pages, featuring dark theme design.

## Overview

This is a static site replication of [miruvor.me](https://miruvor.me) with a dark theme. It uses Jekyll with Markdown files for content, making it easy to write and publish new posts.

## Features

- ✨ **Minimalist Design**: Clean, distraction-free reading experience
- 🌙 **Dark Theme**: Easy on the eyes with carefully chosen colors
- ⚡ **Lightning Fast**: No JavaScript frameworks, pure HTML/CSS
- 📝 **Markdown-First**: Write content in simple Markdown
- 📱 **Fully Responsive**: Works perfectly on all devices
- 🏷️ **Tag Support**: Organize posts with tags
- 🔍 **Search Functionality**: DuckDuckGo integration for searching posts
- 📦 **Zero Dependencies**: No external libraries or frameworks

## Structure

```
├── _config.yml           # Site configuration
├── _includes/            # Reusable components
│   ├── head.html        # HTML head section
│   └── nav.html         # Navigation menu
├── _layouts/            # Page templates
│   ├── default.html     # Base layout
│   └── post.html        # Blog post layout
├── _posts/              # Blog posts (Markdown files)
├── assets/
│   └── css/
│       └── style.css    # All styling
├── pages/               # Static pages
│   ├── blog.md         # Blog listing
│   ├── archives.md     # Archive view
│   ├── founder.md      # Founder page
│   ├── search.md       # Search page
│   └── tags.md         # Tag listing
└── index.md            # Home page
```

## How to Use

### Adding New Blog Posts

1. Create a new Markdown file in the `_posts/` directory
2. Name it using the format: `YYYY-MM-DD-title.md`
3. Add front matter at the top:

```markdown
---
title: "Your Post Title"
tags: [tag1, tag2]
---

Your content here...
```

4. Commit and push to GitHub - the site updates automatically!

### Editing Pages

- **Home**: Edit `index.md`
- **Founder**: Edit `pages/founder.md`
- **Other pages**: Edit files in the `pages/` directory

### Configuration

Edit `_config.yml` to change:

- Site title and description
- URL settings
- Permalink structure

## Deployment

This site is designed for GitHub Pages:

1. Push your changes to your GitHub repository
2. Enable GitHub Pages in repository Settings
3. Select the branch (usually `main`) and root directory
4. Your site will be live at `https://username.github.io/repo-name/`

## Design Philosophy

- **Content First**: Typography and readability are prioritized
- **Performance**: Sub-second load times, minimal assets
- **Accessibility**: Semantic HTML, proper contrast ratios
- **Maintainability**: Clean, well-commented code

## Color Scheme (Dark Theme)

- Background: `#0d1117`
- Foreground: `#e6edf3`
- Muted: `#8b949e`
- Links: `#58a6ff`

## Browser Support

Works on all modern browsers:

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers

## License

Content is owned by Miruvor. Code structure is freely available for use.

## Contact

For questions or collaboration opportunities, visit [miruvor.me](https://miruvor.me)
