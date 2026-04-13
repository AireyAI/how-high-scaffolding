# How High Scaffolding — "Steel & Shadow" Website Design

## Overview
Single-page marketing website for How High Scaffolding, a Carlisle-based scaffolding company covering the full UK. The site drives enquiries (quote form + phone) while showcasing completed work. Dark industrial aesthetic with amber CTAs.

## Business Details
- **Name:** How High Scaffolding
- **Location:** Carlisle, UK-wide coverage
- **Phone:** 07944362960
- **Services:** Residential scaffolding, commercial scaffolding, safety netting, shrink wrapping, permanent handrails (tin roofs for solar)
- **Logo:** HH scaffolding structure logo (provided, black on white — will invert to white on dark)

## Tech Stack
- Single `index.html`, all styles inline via Tailwind CDN
- GSAP + ScrollTrigger + animations.js (AireyAI toolkit)
- Fonts: Bebas Neue (headings) + Inter (body) via Google Fonts
- No frameworks, no build step
- Images: Nano Banana AI-generated for hero/features, placeholder slots for 70+ real photos to be added later
- Video: Veo3-generated hero background + showcase section video

## Color Palette
| Token       | Hex       | Usage                        |
|-------------|-----------|------------------------------|
| Base        | #0A0A0A   | Page background              |
| Surface     | #141414   | Cards, elevated sections     |
| Elevated    | #1A1A1A   | Hover states                 |
| Primary     | #E87A1E   | CTAs, accent lines, icons    |
| Primary Hover | #FF9642 | Button hover                 |
| Text Primary | #FFFFFF  | Headings                     |
| Text Secondary | #A0A0A0 | Body text                   |
| Footer      | #080808   | Footer background            |

## Typography
- **Headings:** Bebas Neue, tracking -0.03em, uppercase
- **Body:** Inter, line-height 1.7, #A0A0A0
- **CTA Buttons:** Inter 600 weight, uppercase, letter-spacing 0.05em

## Sections (top to bottom)

### 1. Navigation (fixed)
- Transparent → solid #0A0A0A on scroll
- Left: HH logo (white)
- Center: Services | About | Gallery | Contact (anchor links)
- Right: Phone number (click-to-call) + "Get a Quote" amber button
- Mobile: hamburger → full-screen dark overlay menu

### 2. Hero (100dvh)
- Veo3 video background: drone shot panning around scaffolding at golden hour
- Overlay: linear-gradient from-black/70 to-black/40
- Content (centered):
  - HH logo fade-in
  - H1: "Built to Reach Any Height" — `data-split="chars"`
  - Subtitle: "Scaffolding, Safety Netting & Specialist Access Solutions — Carlisle to Nationwide" — `data-appear`
  - Two CTAs: "Get a Free Quote" (amber filled) + "Call Now" (white outline) — both `data-magnetic`
- Video layer gets `data-parallax="-50"`

### 3. Services (6-card grid)
- Heading: "What We Do" — `data-reveal="fade-up"`
- 3x2 grid (1 col mobile), `data-stagger-parent`
- Cards: #141414 bg, amber left border, icon top, title, short description
- Each card: `data-stagger-child` + `data-tilt`
- Services:
  1. Residential Scaffolding — Home builds, extensions, renovations
  2. Commercial Scaffolding — Large-scale projects, industrial sites
  3. Safety Netting — Fall protection systems for any height
  4. Shrink Wrapping — Weather protection for roofing projects
  5. Permanent Handrails — Tin roof handrails for safe solar installation
  6. Nationwide Coverage — Based in Carlisle, covering the full UK

### 4. About / Why Choose Us
- Split layout: image left (55%), text right (45%)
- Image: Nano Banana generated — professional scaffolding team on site, `data-parallax="-80"`
- Heading: "Why How High?" — `data-reveal="fade-right"`
- 4 icon bullets: Fully Insured, CITB Certified, Fast Turnaround, UK-Wide Coverage
- Short business ethos paragraph
- Stats row (4 items): "500+" projects, "15+" years, "100%" safety record, "UK-Wide" coverage
  - All stats use `data-counter` with appropriate suffixes

### 5. Gallery
- Heading: "Our Work" — `data-reveal="fade-up"`
- Filter tabs: All | Residential | Commercial | Specialist
- Masonry grid, 8-12 initial slots
- Nano Banana placeholders until real photos are uploaded
- Lightbox on click (CSS/JS based, no library)
- Grid uses `data-stagger-parent`, items use `data-stagger-child`

### 6. Video Showcase
- Full-width section, darker bg (#080808)
- Heading: "See Us In Action" — `data-split="words"`
- Veo3 video: cinematic scaffolding build / timelapse
- Large play button overlay, video loads on click
- `data-reveal="zoom"` on the video container

### 7. Testimonials
- 3 testimonial cards, horizontal layout (carousel on mobile)
- Star ratings (amber), quote text, customer name, location
- Placeholder content initially
- `data-reveal="fade-up"` on each card

### 8. Contact / Quote Form
- Background: #111111
- Split: form left (50%), contact info right (50%)
- Form fields: Name, Phone, Email, Service Required (dropdown with 5 services), Project Details (textarea)
- Submit button: amber, full-width, `data-magnetic`
- Right side: phone (click-to-call icon + number), email placeholder, "Based in Carlisle — Covering the Full UK", Google Maps embed
- Heading: "Get a Free Quote" — `data-reveal="fade-up"`

### 9. Footer
- Background: #080808
- HH logo (small), nav links row, phone, email
- Social media icon placeholders (Facebook, Instagram)
- "Built by AireyAI" credit line
- Copyright: "2026 How High Scaffolding. All rights reserved."

## Animations (full toolkit usage)
- Hero heading: `data-split="chars"`
- Hero subtitle + CTAs: `data-appear` with staggered delays
- All section headings: `data-reveal="fade-up"`
- Service cards: `data-stagger-parent/child` + `data-tilt`
- Stats: `data-counter`
- All buttons/CTAs: `data-magnetic`
- Images: `data-parallax`
- Gallery grid: `data-stagger-parent/child`
- Video section: `data-reveal="zoom"`

## SEO & Meta
- Title: "How High Scaffolding | Residential & Commercial Scaffolding | Carlisle, UK"
- Meta description: "Professional scaffolding services across the UK. Based in Carlisle — residential, commercial, safety netting, shrink wrapping & specialist access solutions. Get a free quote today."
- Open Graph tags with hero image
- Canonical URL placeholder

## Accessibility
- Semantic HTML (nav, main, section, footer)
- Aria labels on interactive elements
- Focus-visible states on all clickable elements
- Sufficient contrast (white/amber on dark backgrounds)
- Touch targets minimum 44px

## Performance
- Lazy load all images below the fold
- Preconnect to Google Fonts CDN
- Defer GSAP scripts
- Video: poster image, load on interaction only

## Image Generation Plan
- **Nano Banana:** Hero fallback image (scaffolding at golden hour), team photo for About section, 8 gallery placeholders (various scaffolding scenarios)
- **Veo3:** Hero background video (drone shot of scaffolding), showcase section video (scaffolding build timelapse)

## Form Handling
- Frontend validation (required fields, email format, phone format)
- Form submission: mailto fallback initially, can wire up to backend later
- Success state: inline confirmation message
