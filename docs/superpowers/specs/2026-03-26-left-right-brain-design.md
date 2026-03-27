# Left Brain / Right Brain Landing Page

## Overview

Split the site into two distinct experiences accessed from a landing page that divides the screen into left and right halves. The left brain represents Andrew's professional, engineering-focused side. The right brain represents his creative, playful side (the existing TV experience).

## Landing Page (`index.html`)

Full viewport, no scroll, split down the middle.

### Left Half
- Background: dark navy (`#0f1f3d`)
- Professional headshot (andrew.png) with subtle grayscale filter
- "Left Brain" heading in clean serif (Playfair Display)
- Tagline: "15 years. Billions in payments. Battle-tested."
- Hover: expands to ~55% width, subtle brightness increase
- Click navigates to `/professional/`

### Right Half
- Background: warm dark (`#1a1a1a`), cartoon character (v2/hello.png)
- "Right Brain" heading in monospace (Courier New)
- Tagline: "Turn the dial. See what's on."
- Hover: expands to ~55% width, subtle static flicker
- Click navigates to `/creative/`

### Shared Elements
- Andrew's name centered at the top, spanning both halves
- Thin divider line between halves
- Responsive: on mobile (<768px), stack vertically (left on top, right below)

## Left Brain — Professional (`/professional/index.html`)

Clean, scrollable multi-section page. Dark navy/white palette. No TV theme.

### Sections
1. **Hero** — Name, title ("Software Engineer & AI Implementation Consultant"), professional headshot, one-liner, CTA button to contact
2. **Experience** — Timeline or structured layout. Fintech/financial services focus. Brands: Twitch, CBS, Sling TV. Super Bowl-scale systems. Billions in annual payment volume. Startup-to-IPO lifecycle.
3. **Services** — Three cards: Custom Software Development, AI Implementation, Technical Consulting. Same copy as existing, professional styling.
4. **Teaching** — 300+ students taught, helping people land first tech jobs.
5. **Portfolio** — Three project cards (Frontier Relay, Nested Academy, A(i) Poignant Guide) in clean layout with links.
6. **Contact** — Form + email link.
7. **Footer** — Copyright + "Visit the right brain →" link.

### Design Language
- Colors: navy (#0f1f3d), white (#ffffff), gold accent (#b8952a)
- Fonts: Playfair Display for headings, Inter for body
- No monospace, no TV references, no scanlines, no test patterns
- Clean borders, subtle shadows, generous whitespace

## Right Brain — Creative (`/creative/index.html`)

The existing TV experience moved here unchanged:
- TV frame viewport
- 5 channels (Hero/newscast, Services, Experience, Portfolio, Contact)
- Dial navigation, curtain power-on, static transitions
- CRT scanlines, test pattern dividers, monospace fonts
- "Visit the left brain →" link accessible somewhere on screen

## File Architecture

### New Files
- `index.html` — Landing page (split screen)
- `professional/index.html` — Left brain professional site
- `assets/css/landing.css` — Landing page styles
- `assets/css/professional.css` — Professional page styles

### Moved Files
- Current `index.html` content → `creative/index.html`
- Current TV-specific CSS stays in `main.css` (used by creative page)

### Shared
- `_layouts/default.html` — Remains the layout; landing and professional pages use it
- `_includes/nav.html` — Shown on professional page, hidden on TV/landing
- `_includes/footer.html` — Shown on professional page, hidden on TV/landing

## Mobile Behavior

- **Landing page**: Stacks vertically. Left brain on top, right brain below. Each takes 50vh.
- **Professional page**: Fully responsive, standard mobile layout.
- **Creative page**: Existing mobile fallback (scrollable site, no TV frame).
