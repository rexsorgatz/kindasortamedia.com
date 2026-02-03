# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the portfolio website for Kinda Sorta Media (KSM), a digital consulting agency. It's a single-page static site with no build system - changes are made directly to the HTML file and deployed via Git.

## Development

**No build step required.** The site is pure HTML/CSS/JS with no dependencies.

- Edit `index.html` directly (contains inline CSS and JS)
- Test by opening index.html in a browser
- Deploy by pushing to the main branch

## Deployment

Site is hosted on **Cloudflare Pages** with automatic deployments on push to main.

- **Dashboard**: Cloudflare > Developer Platform > Workers & Pages > kindasortamedia-com
- **Domains**: kindasortamedia.com, kindasortamedia-com.pages.dev
- Deployments typically complete in ~20 seconds
- If a deployment fails, retry from the dashboard (usually transient Cloudflare errors)

## Architecture

### Page Sections
- **#alpha** - Logo and agency description
- **#beta** - Client portfolio with skills matrix (sticky header)
- **#gamma** - Footer with animated floating clouds

### Skills Matrix (14 columns)
Each client displays a row of boxes indicating services provided:
1. Research, 2. Strategy, 3. Product Dev, 4. Design, 5. Engineering, 6. Content Dev, 7. Staffing, 8. Project Mgmt, 9. Business Dev, 10. Marketing, 11. Press, 12. Audience Dev, 13. Fundraising, 14. IT

Client entries use `<span class="tall-box">` for active skills and `<span class="empty-tall-box">` for inactive.

### Adding a New Client
Add an `<article class="client">` block inside `.content` with:
- `<h3 class="visually-hidden">` for the client name
- `<div class="client-image">` with logo (240x69px, lazy loaded)
- `<div class="client-skills">` with 14 spans (tall-box or empty-tall-box)
- `aria-label` on client-skills listing the services provided

### Key JavaScript Features
- **IntersectionObserver**: Triggers fade-in animation when client rows enter viewport
- **Floating clouds**: 7 animated GIFs moving across the footer at random speeds (60-240 px/sec)
- **Sticky header fix**: Compensates for mobile browser chrome on touch devices

### CSS Variables
```css
--max-width: 960px
--color-black: #000000
--color-white: #ffffff
--color-gray-light: #dddddd
--color-gray-text: #999999
--color-bg: #f5f6fa
```

## Assets

- **Logos**: `img/logo-*.jpg` (client logos, 240x69px standard)
- **Clouds**: `img/cloud1-7.gif` (animated floating elements)
- **Fonts**: `fonts/Gotham*.woff2` (Gotham typeface family)
