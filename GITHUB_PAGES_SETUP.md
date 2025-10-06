# GitHub Pages Setup Guide

This document explains the GitHub Pages setup for the Installation repository.

## Structure Created

The following structure has been set up:

```
Installation/
├── _config.yml          # Jekyll configuration with primer theme
├── index.md             # Main landing page for GitHub Pages
├── logo/                # Directory for logo files
│   └── .gitkeep
├── images/              # Directory for image files
│   └── .gitkeep
└── README.md            # Repository README (excluded from GitHub Pages)
```

## Components

### 1. `_config.yml`
The Jekyll configuration file includes:
- **Theme**: `jekyll-theme-primer` (with `remote_theme` for GitHub Pages compatibility)
- **Site metadata**: Title, description, author information
- **Plugins**: jekyll-remote-theme and jekyll-seo-tag
- **Markdown processor**: kramdown
- **Exclusions**: README.md is excluded from the site build

### 2. `index.md`
The main landing page with:
- Proper Jekyll front matter (layout: default)
- Welcome message and introduction
- Sections for WSL2 and Conda installation guides
- Links to resources
- Auto-updating timestamp

### 3. Directories

#### `logo/`
Place your logo files here for use in the GitHub Pages site. Examples:
- `logo/site-logo.png`
- `logo/banner.svg`

Reference logos in your markdown files:
```markdown
![Logo](logo/site-logo.png)
```

#### `images/`
Place all images referenced in your installation guides here. Examples:
- `images/wsl2-screenshot.png`
- `images/conda-installation-step1.jpg`

Reference images in your markdown files:
```markdown
![WSL2 Installation](images/wsl2-screenshot.png)
```

## Adding Your Installation Guides

### For WSL2 Installation Guide:
1. Add your markdown file: `wsl2-installation.md`
2. Include Jekyll front matter at the top:
```yaml
---
layout: default
title: WSL2 Installation Guide
---
```
3. Reference images as: `![Description](images/your-image.png)`

### For Conda Installation Guide:
1. Add your markdown file: `conda-installation.md`
2. Include Jekyll front matter at the top:
```yaml
---
layout: default
title: Conda Installation Guide
---
```
3. Reference images as: `![Description](images/your-image.png)`

### Updating the Index
After adding your guides, update `index.md` to link to them:
```markdown
### [Windows Subsystem for Linux 2 (WSL2)](wsl2-installation)
Learn how to set up WSL2 on your Windows machine.

### [Conda Installation](conda-installation)
Step-by-step guide for installing Conda.
```

## Enabling GitHub Pages

1. Go to your repository settings on GitHub
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select the branch containing these files (usually `main` or `master`)
4. Select `/ (root)` as the folder
5. Click "Save"
6. Your site will be published at: `https://skillsunfold.github.io/Installation/`

## Theme Customization

The Primer theme provides a clean, GitHub-style interface. To customize:
- Add custom CSS in `assets/css/style.scss`
- Modify layouts by creating files in `_layouts/`
- See [Primer theme documentation](https://github.com/pages-themes/primer)

## Best Practices

1. **Images**: Use descriptive filenames and alt text for accessibility
2. **File naming**: Use lowercase with hyphens (e.g., `wsl2-installation.md`)
3. **Front matter**: Always include layout and title in your markdown files
4. **Links**: Use relative links for internal pages (no `.md` extension in links)
5. **Testing**: Preview locally with Jekyll before pushing changes

## Local Testing (Optional)

To test your site locally:
```bash
gem install bundler jekyll
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000` in your browser.

## Support

For issues or questions:
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Primer Theme Repository](https://github.com/pages-themes/primer)
