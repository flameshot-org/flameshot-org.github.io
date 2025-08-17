# Flameshot Website Development Instructions

Flameshot.org is a static documentation website built with Zola (Rust-based static site generator) for the Flameshot screenshot application project. This site serves as the main landing page and documentation hub.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Quick Setup and Build
- Download Zola: `curl -L https://github.com/getzola/zola/releases/download/v0.17.2/zola-v0.17.2-x86_64-unknown-linux-gnu.tar.gz | tar xz`
- Build the site: `./zola build` -- takes <1 second. Build warnings about highlight languages are normal and non-critical.
- Start development server: `./zola serve --interface 0.0.0.0` -- starts in <1 second, serves on port 1111
- Access the site: Open `http://127.0.0.1:1111` in browser

### No Complex Dependencies Required
- **NO npm install needed** - This is not a Node.js project
- **NO package managers required** - Only Zola binary needed
- **NO build tools like webpack/gulp** - Zola handles everything
- **NO test framework** - Validation is manual through browser testing

## Validation

### Always Manually Validate Changes
After making any content or code changes, perform these validation steps:

1. **Build Validation**: Run `./zola build` and check for any NEW errors (existing highlight language warnings are normal)
2. **Content Navigation**: Test these key user flows in browser:
   - Homepage loads with proper Flameshot branding
   - Navigate to `/docs/` and verify documentation sections load
   - Test installation guides: `/docs/installation/installation-linux/`
   - Test key documentation: `/docs/guide/key-bindings/`
   - Verify internal links work properly
3. **Search Functionality**: Test the search feature on any page
4. **Mobile View**: Test responsive design on mobile viewport

### Manual Testing Scenarios
Always test these complete scenarios after changes:
- **New User Flow**: Homepage → Download section → Installation docs → Basic guide
- **Documentation Discovery**: Docs homepage → Installation → Guide → Advanced features
- **Cross-References**: Verify any internal links in modified content work correctly

## Build and Development Commands

### Core Commands
```bash
# Download Zola (run once per environment)
curl -L https://github.com/getzola/zola/releases/download/v0.17.2/zola-v0.17.2-x86_64-unknown-linux-gnu.tar.gz | tar xz

# Build site (takes <1 second)
./zola build

# Start development server (takes <1 second)
./zola serve

# Start dev server accessible from other machines
./zola serve --interface 0.0.0.0

# Build with drafts included
./zola build --drafts
```

### Expected Timing
- **Build time**: <1 second - NEVER CANCEL, but timeouts unnecessary
- **Dev server startup**: <1 second - NEVER CANCEL, but timeouts unnecessary
- **Content hot-reload**: Near-instant when editing markdown/sass files

## Project Structure and Key Files

### Content Structure
```
content/
├── _index.md              # Homepage content
├── docs/
│   ├── _index.md          # Documentation homepage
│   ├── installation/      # Installation guides for all platforms
│   ├── guide/            # User guides and tutorials
│   ├── advanced/         # Advanced configuration and CLI options
│   └── more/             # Additional resources
└── donate/               # Donation page
```

### Styling and Templates
```
sass/
├── main.scss             # Main stylesheet entry point
├── bootstrap/            # Bootstrap framework (v5.2.0)
├── components/           # Reusable component styles
└── layouts/             # Layout-specific styles

templates/
├── index.html           # Homepage template
├── base.html            # Base template for all pages
├── docs/                # Documentation-specific templates
└── macros/              # Reusable template macros
```

### Configuration Files
```
config.toml              # Main site configuration
theme.toml               # Theme metadata
.github/workflows/build.yml  # CI/CD pipeline for GitHub Pages
```

## Common Development Tasks

### Content Editing
- Edit markdown files in `/content/` directory
- Use TOML frontmatter for page metadata
- Images go in `/static/media/content/docs/[section]/[page-name]/`
- Follow existing image naming conventions: `YYYY-MM-DD_HH-MM_description.png`

### Styling Changes
- Edit Sass files in `/sass/` directory
- Sass auto-compiles during `zola serve`
- Main entry point: `/sass/main.scss`
- Bootstrap customizations in `/sass/bootstrap/`

### Template Modifications
- Edit HTML templates in `/templates/` directory
- Use Tera templating syntax (similar to Jinja2)
- Test template changes with `zola serve`

## CI/CD and Deployment

The site deploys automatically via GitHub Actions:
- **Trigger**: Push to `master` branch
- **Action**: `.github/workflows/build.yml`
- **Target**: GitHub Pages (`gh-pages` branch)
- **Build time**: ~1 minute in CI environment

For pull requests, the action only validates that the build succeeds without deploying.

## Frequently Accessed File Locations

### Documentation Files (Most Common Edits)
```bash
# Installation guides
ls content/docs/installation/
# Output: installation-linux.md, installation-windows.md, installation-osx.md, source-code.md, development-build.md

# User guides
ls content/docs/guide/
# Output: key-bindings.md, troubleshooting.md, wayland-help.md, windows-help.md, imgur_help.md, issue-reporting.md, faq.md

# Advanced topics
ls content/docs/advanced/
# Output: configuration.md, commandline-options.md, protecting-your-privacy.md
```

### Configuration and Build Files
```bash
# Site configuration
cat config.toml

# Main stylesheet
cat sass/main.scss

# Homepage template
cat templates/index.html

# Documentation template
cat templates/docs/section.html
```

## Content Conventions

### Markdown Style
- One sentence per line (except in lists)
- Empty line between paragraphs
- Two empty lines before section headings
- Use American English spelling
- Link complex terms to Merriam-Webster definitions

### Code Blocks
Always specify language for syntax highlighting:
````markdown
```sh
command here
```
````

### Flameshot Button References
Format: Button name first, then icon
```html
<img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/ICON-NAME.svg" />
```

### Image Guidelines
- Place images in `/static/media/content/docs/[section]/[page-name]/`
- Use `#fa0164` color for arrows and markings
- Include alt-text in double quotes
- Keep reasonable dimensions (not too wide/tall)

## Troubleshooting Common Issues

### Build Warnings
- Highlight language warnings are normal and can be ignored
- Color contrast warnings in Bootstrap are cosmetic and non-critical

### Development Server Issues
- If port 1111 is busy, kill existing zola processes: `pkill zola`
- Server auto-reloads on file changes - no manual restart needed

### Content Not Updating
- Check markdown frontmatter syntax (TOML format)
- Verify file is in correct directory structure
- Restart dev server if changes don't appear

This site has minimal complexity - most issues stem from markdown formatting or missing files rather than complex build problems.