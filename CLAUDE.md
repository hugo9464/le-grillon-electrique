# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Start development server
hugo server

# Build for production
hugo --minify --gc

# Create new homepage section
hugo new homepage/my-section.md

# Create new standalone page
hugo new my-page.md
```

## Architecture Overview

This is a Hugo static site using the **hugo-scroll** theme - a single-page scrolling theme with multi-language support.

### Content Structure

The site uses two content types:

1. **Homepage sections** (`content/{lang}/homepage/*.md`): Individual sections that combine into the scrolling homepage
   - Ordered by `weight` parameter
   - Can appear in navigation with `header_menu: true`

2. **Standalone pages** (`content/{lang}/*.md`): Traditional pages with their own URLs
   - Example: `content/en/services.md` → `/en/services/`

### Key Configuration Points

**hugo.toml**: Main site configuration
- Theme settings, language setup, contact information
- `disableKinds` is set to create a focused single-page experience

**Content Front Matter Options**:
- `header_image`: Hero section background
- `header_use_video`: Enable video background (requires `custom_header_video.html`)
- `header_logo`: Logo image path
- `weight`: Section ordering
- `header_menu`: Show in navigation

### Customization Approach

1. **CSS Overrides**: Create `/layouts/partials/custom_head.html` to override CSS variables
2. **Video Backgrounds**: Add `/layouts/partials/custom_header_video.html` 
3. **Icons**: Use FontAwesome v6.6.0 icons with `{{< icon name="icon-name" >}}` shortcode

### Multi-language Structure

- Languages defined in `hugo.toml` (currently `en` and `de`)
- Content separated by language: `/content/en/` and `/content/de/`
- Language switcher enabled by default

### Theme Integration

The theme is included as a git submodule at `/themes/hugo-scroll/`. Site-specific overrides go in the root directories (`/layouts/`, `/assets/`, `/static/`).