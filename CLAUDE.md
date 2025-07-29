# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

This is a Ghost theme based on the Source theme for Lukas Zangerl's coaching business website.

### Essential Commands

```bash
# Install dependencies (use legacy peer deps due to postcss version conflicts)
npm install --legacy-peer-deps

# Development (requires gulpfile.js - currently missing)
npm run dev

# Build the theme
npm run build

# Run theme validation
npm test

# Create deployable zip file
npm run zip
```

### Important Build Notes

⚠️ **The gulpfile.js is currently missing from this repository.** This means:
- Automated CSS/JS compilation is not available
- Manual file copying is required for development
- The npm scripts reference gulp but will fail without the gulpfile

**Manual Development Workflow:**
1. Edit source files directly:
   - CSS: `assets/css/screen.css`
   - JS: `assets/js/*.js`
2. For production, manually copy to built directory:
   - Copy `assets/css/screen.css` → `assets/built/screen.css`
   - Concatenate JS files → `assets/built/source.js`

## Architecture Overview

### Template Structure
This German-language Ghost theme uses Handlebars templating with a component-based architecture:

- **Base Template**: `default.hbs` - Defines HTML structure, includes navigation and footer
- **Page Templates**: 
  - `home.hbs` - Landing page with profile section
  - `post.hbs`, `page.hbs` - Content pages
  - `tag.hbs`, `author.hbs` - Archive pages
- **Components**: `partials/components/` - Reusable UI elements
- **Icons**: `partials/icons/` - SVG icons as Handlebars partials

### Landing Page Implementation
The theme features a custom "Landing" header style optimized for personal branding:
- **Profile Container**: `.gh-landing-container` - Personal greeting and tagline
- **Profile Image**: `.gh-landing-image` - Circular profile photo (280px, responsive)
- **Newsletter Integration**: Built-in email subscription form
- **Responsive Design**: Mobile-first approach with desktop optimizations

### CSS & JavaScript
- **CSS**: Single large file at `assets/css/screen.css` (28,000+ lines)
- **JavaScript**: Modular structure in `assets/js/`
  - Core functionality: Navigation, lightbox, pagination
  - External libraries: PhotoSwipe, imagesloaded, reframe
- **Build Output**: `assets/built/` directory for production files

### Theme Configuration
Extensive customization options via Ghost admin (defined in `package.json`):
- Navigation layouts (3 options)
- Header styles (Landing, Highlight, Magazine, Search, Off)
- Typography (fonts for titles and body)
- Colors and background images
- Post feed layouts (List/Grid)
- Publication info sidebar

## Development Guidelines

1. **Ghost Version**: Requires Ghost 5.0.0+
2. **Language**: All content in German for Lukas Zangerl's coaching business
3. **Profile Image**: Currently hardcoded in `partials/components/header-content.hbs`
4. **Testing**: Use `npm test` to validate theme with gscan
5. **Deployment**: Create zip with `npm run zip` for Ghost upload

## Git Workflow Integration

When making commits in this repository:
1. The CLAUDE.md file should be reviewed and updated if needed
2. Use descriptive commit messages following the repository's style
3. All commits will include Claude's co-authorship signature

## Missing Dependencies

To fully restore development capabilities, you'll need:
1. A proper `gulpfile.js` with tasks for:
   - CSS compilation from source files
   - JavaScript concatenation and minification
   - Watch mode for development
   - Build task for production
2. PostCSS configuration for CSS processing