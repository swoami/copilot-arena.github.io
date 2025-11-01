# Copilot Instructions - Professional CV Website

## Project Overview
This is a **static single-page CV website** for GitHub Pages. The site is desktop-first, using pure HTML5/CSS3/vanilla JavaScript with no build tools or frameworks. All CV content is defined in `README.md`.

## Architecture & Key Decisions

- **Single HTML file**: All sections (About, Skills, Experience, Projects, Contact) live in `my-cv-site/index.html`
- **No build process**: Pure HTML/CSS/JS - no npm, webpack, or bundlers
- **Assets location**: Images stored in `my-cv-site/assets/` (currently contains background images)
- **Deployment**: GitHub Pages serves from root or `/docs` folder (configure in repo settings)
- **CV content source**: Extract all professional details from `README.md` "CV Content" section

## Development Workflow

### Local Development
```powershell
# Serve locally (no special server needed)
cd my-cv-site
python -m http.server 8000
# Or use VS Code Live Server extension
```

### Deployment
1. Commit changes to `main` branch
2. GitHub Pages auto-deploys from configured folder
3. Verify at `https://<username>.github.io/<repo-name>/`

## File Structure Conventions

```
my-cv-site/
  index.html        # Single-page site
  styles.css        # All styles (or split into sections)
  script.js         # Optional: smooth scroll, animations
  assets/           # Images, icons
```

## Coding Patterns

### HTML Structure
- Use semantic HTML5: `<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`
- Each CV section gets a `<section id="section-name">` for anchor navigation
- Sticky nav should use `<nav>` with fixed positioning
- Experience timeline: use ordered list `<ol>` or `<article>` per role

### CSS Approach
- **Desktop-first**: Base styles for desktop (1200px+), optional media queries for smaller screens
- **Layout**: CSS Grid for main sections, Flexbox for nav and cards
- **Colors**: Use CSS custom properties (`:root` variables) for consistent palette
- **Animations**: CSS transitions for hover effects, `scroll-behavior: smooth` for navigation
- **Typography**: Bold headings with clear hierarchy (h1 = name, h2 = section titles)

Example color palette:
```css
:root {
  --primary: #2c3e50;
  --accent: #3498db;
  --background: #ecf0f1;
  --text: #34495e;
}
```

### JavaScript (if needed)
- Keep minimal: smooth scroll polyfill, intersection observer for animations
- No dependencies: vanilla JS only
- Optional: scroll-triggered section highlighting in nav

## Content Guidelines

### Extracting CV Data from README.md
- **Name**: "John Doe, Senior Software Developer"
- **Languages**: English, Spanish
- **Experience**: Parse the timeline format (e.g., "JAN 2022 – Current")
- **Certifications**: 4 Microsoft certifications listed
- **External links**: Add placeholders for GitHub and LinkedIn URLs

### Writing Style
- Concise bullet points (see README examples)
- Action-oriented (e.g., "Development of...", "Migration of...")
- Highlight technologies: Azure, React, Angular, SQL Server, etc.

## Design Requirements (from README)

✅ Modern, visually striking with smooth animations  
✅ Bold typography and clean minimal layout  
✅ Sleek color palette with subtle gradients  
✅ Smooth scroll and hover effects  
✅ Sticky navigation bar  
✅ Sections: About, Skills, Experience, Projects, Contact  

## Common Tasks

### Adding a New Section
1. Add `<section id="new-section">` in `index.html`
2. Add nav link: `<a href="#new-section">New Section</a>`
3. Style in `styles.css` following grid/flexbox pattern
4. Test scroll behavior

### Updating Experience
1. Reference `README.md` "CV Content" for source data
2. Maintain chronological order (newest first)
3. Format: Company name (bold), role (italic), date range, bullet points

### Deploying Changes
- No build step needed
- Commit directly to `main`
- Changes appear on GitHub Pages within 1-2 minutes

## Important Constraints

❌ No backend or APIs  
❌ No user authentication  
❌ No external form handling (unless using Google Forms embed)  
❌ No npm packages or frameworks  
❌ Mobile responsiveness optional (desktop-first)  

## Testing Checklist

- [ ] All sections render correctly on desktop (1920px, 1366px)
- [ ] Sticky nav works and links scroll to sections
- [ ] Hover effects on interactive elements
- [ ] Images load from `assets/` folder
- [ ] External links open in new tabs (`target="_blank"`)
- [ ] No console errors in browser DevTools

## When Modifying Code

1. **Check README.md first** - CV content may have been updated
2. **Keep it simple** - Avoid over-engineering for a static site
3. **Test locally** - Use Live Server or Python's http.server
4. **Validate HTML** - Use W3C validator before committing
5. **Preserve visual style** - Maintain color palette and typography choices
