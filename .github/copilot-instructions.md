# Consentia Codebase Instructions for AI Agents

## Project Overview
A static HTML5 website for Consentia, a UK GDPR advisory service. The site guides UK individuals through three core scenarios: recovering hacked social media accounts, removing unwanted personal data from the internet, and handling company refusals to delete data.

## Architecture & Core Patterns

### Page Structure
- **Landing page**: `index.html` - Hub with 3 service sections + "other issues" list
- **Service pages**: `recover-hacked.html`, `remove-data.html`, `company-refusing.html` - Detailed guidance with GDPR legal references
- **Contact/assessment**: `contact.html` - Google Forms iframe + direct contact details
- All pages follow identical header structure: logo + headline + subheadline

### Consistent Component Patterns
Each service page uses this standard layout:
```html
<header class="main-header-left">
  <img src="images/logo.png" alt="Consentia Logo" class="logo-left">
  <div class="header-text">
    <h1>[Service Title]</h1>
    <p>[Brief description]</p>
  </div>
</header>

<section class="service-section">
  <div class="service-content">
    <img src="images/[icon].png" alt="[Icon Alt]" class="service-image">
    <div class="service-text">
      <!-- Content with .btn links -->
    </div>
  </div>
</section>
```

### CSS Conventions
- **Semantic class names**: `.service-section`, `.service-content`, `.service-text`, `.service-image`, `.btn`
- **Color scheme**: Light blue base (`#cce6ff`), alternate section background (`#f0f8ff`), text (`#003366`), links/buttons (`#0066cc`)
- **Layout**: Flexbox-based responsive design with `gap: 40px` between image and text
- **Alternating sections**: Use `.alt-bg` class on every other section for visual hierarchy
- **Hover effects**: Images scale 1.05, buttons darken on hover (standard transitions 0.3s)

### Navigation Pattern
Every page links back to `index.html` and forward to `contact.html` using consistent `.btn` elements. No top navbar—rely on header logo or explicit navigation buttons.

## Specific Development Guidelines

### When Adding Service Pages
1. Copy structure from existing service pages (e.g., `recover-hacked.html`)
2. Include GDPR legal references (Articles 6, 12, 15, 17, 32) where relevant
3. Alternate `.service-section` background using `.alt-bg` class
4. Use service icons from `images/` directory (120px x 120px fits style)
5. Always link to `contact.html` with text "Free Assessment" and back to `index.html`

### When Modifying CSS
- Keep all color values consistent with existing palette (don't add new colors without approval)
- Maintain 60px vertical padding on sections for consistent spacing
- Use transition effects only where established (images, buttons) to avoid UI bloat
- Preserve mobile responsiveness: sections must flex-wrap properly with 20px horizontal padding

### Content & Legal Consistency
- User-facing content is action-oriented: "We can help," "we guide," "you have rights"
- All pages reference UK GDPR as the legal framework (mention Article numbers when explaining user rights)
- Forms integrate via **Google Forms iframe** (contact.html), not server-side forms
- Direct contact details in contact.html: `contact@consentia.uk` and `07404790439`

### When Adding Images
- Place all images in `images/` directory
- Use descriptive alt text (e.g., "Hacked Account Icon", "Company Refuse Icon")
- Service section icons should be 120px × 120px with transparent backgrounds
- Reference style: `<img src="images/[name].png" alt="[Descriptive Text]" class="service-image">`

## Known Technical Details
- No JavaScript or backend—pure static HTML5 + CSS
- Meta tags standardized: UTF-8 charset, viewport for mobile responsiveness (`width=device-width, initial-scale=1.0`)
- All pages use relative paths for CSS (`href="style.css"`) and images (`src="images/..."`)
- Google Forms integration: embedded via iframe (see `contact.html` line with `forms.gle`)

## Common Tasks

| Task | Approach |
|------|----------|
| Add new service offering | Create page following structure in `recover-hacked.html`, update `index.html` with new section and link |
| Update button colors/styling | Modify `.btn` and `.btn:hover` in `style.css` only |
| Adjust spacing between sections | Modify `padding: 60px 20px` on `.service-section` in `style.css` |
| Change color scheme globally | Update color variables in top of `style.css` (body, .alt-bg, .btn, links) |
| Add/modify contact form | Edit iframe src in `contact.html` or add direct contact channels |
