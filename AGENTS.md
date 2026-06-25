# AGENTS.md

This file provides guidance for AI agents working on the Fractal Boston website. It documents patterns, conventions, and learnings to ensure consistency across changes.

## Repository Overview

This is a **static website** built with vanilla HTML, CSS, and minimal JavaScript:
- No build process, frameworks, or package managers
- Multi-page structure with shared navigation
- Styles: `styles.css` (custom) + `normalize.css` (reset)
- Deployment: GitHub Pages (via `CNAME` file)

## Site Structure

The site is organized into multiple pages with consistent navigation:

### Pages

| Page | Path | Purpose |
|------|------|---------|
| **Home** | `/index.html` | Landing page with hero, activity highlights, and CTAs |
| **Activities** | `/activities/index.html` | Detailed activities (dinners, FBU, coworking) + calendar |
| **About** | `/about/index.html` | Origin story, testimonial, and subscribe form |

### Navigation

All pages share a consistent navigation bar in the header:
```html
<nav>
  <a href="/" class="active">Home</a>
  <span class="nav-separator">✦</span>
  <a href="/activities">Activities</a>
  <span class="nav-separator">✦</span>
  <a href="/about">About</a>
</nav>
```
- Add `class="active"` to the current page's link
- Use absolute paths (`/activities`, not `activities/`)

### Page Layout

Each page uses this structure:
- **Header**: H1 title (linked to home) + navigation bar
- **Content**: Page-specific sections
- **Footer**: Minimal or empty

The site uses a card-based layout with organic, playful shapes:
- Subtle gradients with green tints (`#f0fdf4`)
- Irregular border-radius values
- Decorative shapes and floating animations

## Styling Patterns & Conventions

### Design Philosophy

The site uses an **organic, playful aesthetic** with:
- Irregular border-radius values that feel hand-drawn
- Subtle gradients with green tints (`#f0fdf4`)
- Gentle rotations on elements (`rotate(-0.5deg)`)
- Decorative shapes and floating animations
- Main color: `--main-color: #059669` (green)

### Content Section Classes

Each major content section typically has a custom class (e.g., `.education-block`, `.luma-calendar`, `.coworking-block`) with:

1. **Background gradient** with subtle green tint
2. **Organic border-radius** for uniqueness
3. **Optional h3 styling** for section headings

### Creating a New Section: Step-by-Step

When adding a new content section, follow this pattern:

#### 1. HTML Structure

```html
<div class="your-section-name card">
  <h3>Section Title</h3>
  <p>Your content here...</p>
  <!-- Optional: buttons, links, images -->
</div>
```

#### 2. CSS Styling - Background & Shape

Add a class in `styles.css` with:

```css
.your-section-name {
  background: linear-gradient(XXXdeg, #fefefe 0%, #f0fdf4 100%);
  border-radius: YYpx ZZpx AApx BBpx / CC% DD% EE% FF%;
}
```

**Key points:**
- **Gradient direction**: Vary the angle (105deg, 285deg, etc.) to make each section unique
- **Always use**: `#fefefe` (near-white) to `#f0fdf4` (subtle green tint)
- **Border-radius**: Use 8 values (4 corners with x/y for each) with irregular numbers to create organic shapes
- **Inspiration**: Look at `.education-block` (105deg) and `.luma-calendar` (285deg) for examples

#### 3. CSS Styling - H3 Underline (Optional)

If your section needs a longer h3 underline (like activities sections), add:

```css
.your-section-name h3::after {
  transform: scaleX(0.6) rotate(-0.8deg);
}
```

**Key points:**
- Default h3 underline: `scaleX(0.2)` (short)
- Activities-style underline: `scaleX(0.6)` (longer, more prominent)
- Vary the rotation slightly: `-0.5deg`, `-0.8deg`, `-1.2deg`
- This makes section headings stand out more

### H3 Underline System

The site uses a progressive underline system for h3 elements:

```css
/* Default: short underline for most h3s */
h3::after {
  transform: scaleX(0.2) rotate(-0.5deg);
}

/* Activities sections: longer underline */
.activities-section h3::after {
  transform: scaleX(0.6) rotate(-1.2deg);
}

/* Luma calendar: longer underline */
.luma-calendar h3::after {
  transform: scaleX(0.6) rotate(-0.8deg);
}

/* Stay connected: no underline */
.stay-connected h3::after {
  display: none;
}
```

**When to use longer underlines** (scaleX(0.6)):
- Major content sections with multiple paragraphs
- Sections that introduce new topics/activities
- Anywhere you want extra visual hierarchy

### Call-to-Action (CTA) Patterns

#### Main CTA (Hero Button)

```html
<a href="URL" target="_blank" rel="noopener noreferrer nofollow" class="main-cta">
  <button class="block accent">✨ Text ✨</button>
</a>
```

**Note**: Do NOT add links to `/discord` or any Discord URL anywhere on the site. Access to the Discord is intentionally word-of-mouth only — people should hear about it from a person at a live event. Discord may be *mentioned* in copy where it makes sense, but never *linked*. The `/discord` redirect (`discord/index.html`) stays in place so members told the URL in person can get in.

#### Secondary CTA (Block Button)

```html
<a href="URL" target="_blank" style="text-decoration: none;">
  <button class="block">Button Text</button>
</a>
```

**Key points:**
- Use `style="text-decoration: none;"` to remove underlines from buttons
- Don't over-use emojis in button text unless explicitly requested
- Keep button text concise and action-oriented

### Link Patterns

The site uses two main link patterns:

1. **External links**: Always include `target="_blank" rel="noopener noreferrer nofollow"`
2. **Discord**: Never link to the Discord (`/discord` or any Discord URL). It's word-of-mouth only — see the CTA note above.

## Common Tasks

### Updating CTAs/Links

When updating calls-to-action:
1. Check both hero section and footer
2. Update link URLs and button/link text consistently
3. Ensure proper rel attributes for external links

### Adding Event Content

Follow the pattern in `.activities-section`:
- Use `.event-block` for image galleries
- Use `.event-photo` class for images
- Wrap content in semantic tags

### Styling Guidelines

- **Avoid inline styles** except for rare cases (like removing text-decoration)
- **Use CSS variables**: `var(--main-color)`, `var(--text-color)`, etc.
- **Test responsiveness**: Site has breakpoints at 650px, 480px
- **Keep animations subtle**: Site uses gentle float/wobble animations

## Learnings from Recent Sessions

### Session: Multi-Page Site Restructure (Mar 2026)

**Task**: Split single-page site into multiple pages with navigation

**Changes Made**:
1. Created `/activities/index.html` with all activities content + calendar
2. Created `/about/index.html` with origin story, testimonial, and subscribe form
3. Added navigation bar to all pages (header after h1)
4. Condensed home page to hero + highlights grid + CTA section
5. Added navigation CSS styles (`.nav`, `.nav a`, `.nav-separator`)
6. Added home page highlight styles (`.highlights-grid`, `.highlight-item`)

**Key Insights**:
- Use absolute paths in nav (`/activities` not `activities/`)
- Mark current page with `class="active"` on nav link
- Each page needs its own `<head>` with appropriate title/meta
- JavaScript for forms needs to be duplicated on pages that use them
- Home page should be focused and punchy - detailed content goes on subpages

**New CSS Classes Added**:
```css
/* Navigation */
nav { display: flex; justify-content: center; gap: 0.5rem; }
nav a { padding: 0.8rem 1.6rem; border-radius: organic; }
nav a.active { background: var(--main-color); color: white; }
nav .nav-separator { color: var(--main-color); opacity: 0.3; }

/* Home highlights grid */
.highlights-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); }
.highlight-item { text-align: center; }
.highlight-icon { font-size: 3.5rem; }
```

### Session: Discord Links & Luma Calendar Styling (Jan 2026)

**Task**: Update Discord links and style the Luma calendar section

**Changes Made**:
1. Updated hero "Join the Crew" button: `https://forms.gle/...` → `https://fractal.boston/discord`
2. Updated footer CTA text: "Fill out our interest form" → "Introduce yourself in Discord"
3. Styled `.luma-calendar` section with gradient and border-radius
4. Extended `.luma-calendar h3::after` underline from scaleX(0.2) to scaleX(0.6)
5. Rewrote calendar section copy to be more inviting and concise

**Key Insights**:
- When styling a new section, ALWAYS check if it needs an h3::after adjustment
- Gradient direction matters: reverse it (105deg → 285deg) for visual variety
- Border-radius should have 8 values for organic feel
- Button text should be action-oriented: "Open calendar" not "View the Luma calendar"
- Remove text-decoration from button links with inline style when needed

**Pattern Established**:
```css
/* Step 1: Add gradient background */
.new-section {
  background: linear-gradient(285deg, #fefefe 0%, #f0fdf4 100%);
  border-radius: 22px 30px 18px 35px / 28% 35% 32% 25%;
}

/* Step 2: Extend h3 underline if needed */
.new-section h3::after {
  transform: scaleX(0.6) rotate(-0.8deg);
}
```

## Best Practices

### Before Making Changes
1. Read existing code to understand current patterns
2. Check for similar sections to maintain consistency
3. Use `git diff` before committing to review changes

### Writing Commit Messages
- Keep first line concise (50 chars or less)
- Use imperative mood: "Update" not "Updated"
- Add details in commit body when needed
- Group related changes together

### Testing
- Open `index.html` in a browser to preview changes
- Test on mobile viewport (check responsive styles)
- Verify links open correctly

## Reference Examples

### Well-Styled Sections

**Education Block** (subtle gradient, flowing left):
```css
.education-block {
  background: linear-gradient(105deg, #fefefe 0%, #f0fdf4 100%);
  border-radius: 18px 35px 22px 28px / 32% 25% 40% 35%;
}
```

**Luma Calendar** (subtle gradient, flowing right):
```css
.luma-calendar {
  background: linear-gradient(285deg, #fefefe 0%, #f0fdf4 100%);
  border-radius: 22px 30px 18px 35px / 28% 35% 32% 25%;
}
.luma-calendar h3::after {
  transform: scaleX(0.6) rotate(-0.8deg);
}
```

### Copy Writing Style

- **Concise**: Prefer shorter, punchier sentences
- **Inviting**: Use "Subscribe to stay in the loop" over longer explanations
- **Action-oriented**: "Open calendar" over "View the Luma calendar"
- **Friendly**: Maintain warm, community-focused tone

## Future Considerations

- Keep site lightweight: avoid adding frameworks or build tools
- Maintain organic aesthetic: irregular shapes, gentle animations
- Update CLAUDE.md if project structure changes significantly
- Document new patterns in this file as they emerge
