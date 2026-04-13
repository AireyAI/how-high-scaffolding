# How High Scaffolding — "Steel & Shadow" Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a single-page dark industrial marketing website for How High Scaffolding that showcases services, displays a project gallery, and drives enquiries via quote form and phone.

**Architecture:** Single `index.html` with inline Tailwind styles, GSAP/ScrollTrigger animations via the AireyAI toolkit (`animations.js`), Google Fonts (Bebas Neue + Inter), Nano Banana AI-generated images, and Veo3-generated video. No build step, no frameworks. Served via `serve.mjs` on localhost:3000.

**Tech Stack:** HTML, Tailwind CDN, GSAP + ScrollTrigger, animations.js, Google Fonts, Nano Banana (images), Veo3 (video)

---

## File Structure

```
how-high-scaffolding/
├── index.html          # The entire website (create)
├── animations.js       # AireyAI toolkit (copy from template)
├── serve.mjs           # Dev server (copy from template)
├── screenshot.mjs      # Screenshot tool (copy from template)
├── package.json        # Node config (copy from template, update name)
├── brand_assets/
│   └── logo.png        # HH logo (copy from user-provided image)
├── images/             # Nano Banana generated images
│   ├── hero-bg.jpg
│   ├── team-photo.jpg
│   └── gallery-*.jpg   # 8 gallery placeholder images
├── videos/             # Veo3 generated videos
│   ├── hero-video.mp4
│   └── showcase-video.mp4
├── temporary screenshots/  # Auto-created by screenshot.mjs
└── docs/superpowers/       # Spec + plan docs
```

---

### Task 1: Project Scaffold

**Files:**
- Copy: `AireyAi_projects/new_client_template/animations.js` → `how-high-scaffolding/animations.js`
- Copy: `AireyAi_projects/new_client_template/serve.mjs` → `how-high-scaffolding/serve.mjs`
- Copy: `AireyAi_projects/new_client_template/screenshot.mjs` → `how-high-scaffolding/screenshot.mjs`
- Create: `how-high-scaffolding/package.json`
- Create: `how-high-scaffolding/brand_assets/` directory
- Copy: user-provided logo → `how-high-scaffolding/brand_assets/logo.png`

- [ ] **Step 1: Copy template files**

```bash
cd /Users/kyleairey/AireyAi_projects/how-high-scaffolding
cp ../new_client_template/animations.js ./animations.js
cp ../new_client_template/serve.mjs ./serve.mjs
cp ../new_client_template/screenshot.mjs ./screenshot.mjs
```

- [ ] **Step 2: Create package.json**

```json
{
  "name": "how-high-scaffolding",
  "type": "module",
  "scripts": {
    "serve": "node serve.mjs",
    "screenshot": "node screenshot.mjs"
  },
  "dependencies": {
    "puppeteer": "^22.0.0"
  }
}
```

- [ ] **Step 3: Set up brand assets**

```bash
mkdir -p brand_assets images videos
```

Copy the user-provided HH logo (the image attached in the conversation) to `brand_assets/logo.png`. This is a black-on-white logo — it will be used with a CSS `filter: invert(1)` to display white on the dark background.

- [ ] **Step 4: Install dependencies**

```bash
npm install
```

Expected: `added X packages` — puppeteer installs successfully.

- [ ] **Step 5: Commit scaffold**

```bash
git init
git add -A
git commit -m "chore: scaffold project with template files and brand assets"
```

---

### Task 2: Generate Images with Nano Banana

**Files:**
- Create: `images/hero-bg.jpg`
- Create: `images/team-photo.jpg`
- Create: `images/gallery-1.jpg` through `images/gallery-8.jpg`

Use the `mcp__nano-banana-2__generate_image` tool for each image. Save outputs to `images/`.

- [ ] **Step 1: Generate hero background image**

Prompt: "Dramatic wide-angle photograph of a massive steel scaffolding structure against a golden hour sunset sky. Industrial construction site, warm amber and orange tones, dark steel silhouettes, moody atmosphere, professional construction photography, cinematic lighting"

Save to: `images/hero-bg.jpg`

- [ ] **Step 2: Generate team/about photo**

Prompt: "Professional construction team standing in front of large scaffolding structure on a building site. Workers wearing hard hats and high-visibility vests. Confident pose, industrial background, warm golden hour lighting, professional corporate photography"

Save to: `images/team-photo.jpg`

- [ ] **Step 3: Generate 8 gallery placeholder images**

Generate each with a unique prompt matching the service categories:

1. "Residential house with scaffolding erected around it for renovation work, British suburban setting, professional scaffolding, daylight" → `images/gallery-1.jpg`
2. "Large commercial building covered in scaffolding, construction site, cranes in background, industrial scale, professional photography" → `images/gallery-2.jpg`
3. "Safety netting installed on tall scaffolding structure, close-up of professional fall protection system, construction safety" → `images/gallery-3.jpg`
4. "Scaffolding shrink wrap on a roof, white weather protection sheeting covering scaffolding, British rooftop, professional installation" → `images/gallery-4.jpg`
5. "Permanent metal handrails installed on corrugated tin roof with solar panels, rooftop safety equipment, industrial" → `images/gallery-5.jpg`
6. "Scaffolding on a church or historic building, careful restoration scaffolding around old stone building, heritage construction" → `images/gallery-6.jpg`
7. "Multi-storey scaffolding tower on a new build construction site, professional scaffolding access system, wide shot" → `images/gallery-7.jpg`
8. "Scaffolding on a modern office block, glass building with steel scaffolding, urban construction, professional" → `images/gallery-8.jpg`

- [ ] **Step 4: Commit generated images**

```bash
git add images/
git commit -m "feat: add Nano Banana generated images for hero, about, and gallery"
```

---

### Task 3: Generate Videos with Veo3

**Files:**
- Create: `videos/hero-video.mp4`
- Create: `videos/showcase-video.mp4`

Use the Gemini API Veo3 curl command to generate videos.

- [ ] **Step 1: Generate hero background video**

Prompt: "Cinematic drone shot slowly orbiting around a large steel scaffolding structure at golden hour. Warm sunset light catches the metal framework. Camera moves smoothly from low to high angle revealing the full scale. Industrial construction site, moody atmosphere, amber and orange tones in the sky. No text, no people."

Save to: `videos/hero-video.mp4`

- [ ] **Step 2: Generate showcase video**

Prompt: "Timelapse of scaffolding being erected on a large building. Workers in hard hats and high-vis assembling steel poles and platforms rapidly. Dramatic sky in background, construction site activity, professional scaffolding company at work. Cinematic wide angle, golden hour lighting."

Save to: `videos/showcase-video.mp4`

- [ ] **Step 3: Commit generated videos**

```bash
git add videos/
git commit -m "feat: add Veo3 generated hero and showcase videos"
```

---

### Task 4: Build the HTML — Head, Nav, and Hero

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create index.html with head and meta tags**

Write the `<!DOCTYPE html>` through `</head>` containing:
- Charset, viewport, title: "How High Scaffolding | Residential & Commercial Scaffolding | Carlisle, UK"
- Meta description, Open Graph tags (og:title, og:description, og:image pointing to `images/hero-bg.jpg`, og:type website)
- Canonical URL placeholder
- Google Fonts preconnect + link for Bebas Neue (400;700) and Inter (400;500;600;700)
- Tailwind CDN script with custom config:
  ```js
  tailwind.config = {
    theme: {
      extend: {
        colors: {
          base: '#0A0A0A',
          surface: '#141414',
          elevated: '#1A1A1A',
          primary: '#E87A1E',
          'primary-hover': '#FF9642',
          'text-secondary': '#A0A0A0',
          footer: '#080808',
        },
        fontFamily: {
          display: ['"Bebas Neue"', 'sans-serif'],
          body: ['Inter', 'sans-serif'],
        },
      },
    },
  }
  ```
- SVG noise texture filter in a `<style>` block for grain overlay
- Base styles: `body { background: #0A0A0A; color: #A0A0A0; font-family: 'Inter', sans-serif; }`

- [ ] **Step 2: Add the navigation**

Inside `<body>`, write the fixed navigation:
- `<nav>` with `fixed top-0 w-full z-50` and a transparent background that transitions to `bg-base` on scroll via a small inline JS snippet
- Left: `<img src="brand_assets/logo.png" style="filter:invert(1)" class="h-10">` linked to `#`
- Center: four anchor links — Services (`#services`), About (`#about`), Gallery (`#gallery`), Contact (`#contact`) — styled white, uppercase, Inter 500, with hover underline in amber
- Right: phone link `<a href="tel:07944362960">07944 362 960</a>` + "Get a Quote" button (`bg-primary text-base font-semibold uppercase tracking-wider px-6 py-3 rounded`) linking to `#contact`
- Mobile hamburger: hidden above `lg:`, toggles a full-screen overlay with the same links stacked vertically. Small inline JS to toggle a `.mobile-menu-open` class.

- [ ] **Step 3: Add the hero section**

After `</nav>`, write the hero `<section id="hero">`:
- Full viewport: `min-h-[100dvh] relative flex items-center justify-center overflow-hidden`
- Video background: `<video autoplay muted loop playsinline poster="images/hero-bg.jpg" class="absolute inset-0 w-full h-full object-cover" data-parallax="-50"><source src="videos/hero-video.mp4" type="video/mp4"></video>`
- Dark overlay: `<div class="absolute inset-0 bg-gradient-to-b from-black/70 to-black/40"></div>`
- Content centered: `<div class="relative z-10 text-center px-6 max-w-4xl">`
  - Logo: `<img src="brand_assets/logo.png" style="filter:invert(1)" class="h-24 mx-auto mb-8" data-appear data-appear-delay="0">`
  - H1: `<h1 class="font-display text-5xl md:text-7xl lg:text-8xl text-white uppercase tracking-[-0.03em] mb-6" data-split="chars">Built to Reach Any Height</h1>`
  - Subtitle: `<p class="font-body text-lg md:text-xl text-text-secondary max-w-2xl mx-auto mb-10" data-appear data-appear-delay="0.4">Scaffolding, Safety Netting & Specialist Access Solutions — Carlisle to Nationwide</p>`
  - CTAs: two buttons side by side in a flex-wrap container
    - "Get a Free Quote": `<a href="#contact" class="bg-primary text-base font-semibold uppercase tracking-widest px-8 py-4 rounded inline-block" data-magnetic>Get a Free Quote</a>`
    - "Call Now": `<a href="tel:07944362960" class="border-2 border-white text-white font-semibold uppercase tracking-widest px-8 py-4 rounded inline-block ml-4" data-magnetic>Call Now</a>`
    - Both with `data-appear data-appear-delay="0.6"` and `data-appear-delay="0.8"` respectively

- [ ] **Step 4: Start server and screenshot**

```bash
cd /Users/kyleairey/AireyAi_projects/how-high-scaffolding
node serve.mjs &
node screenshot.mjs http://localhost:3000 hero
```

Read the screenshot from `temporary screenshots/` and verify: dark background, video/poster image visible, logo white, heading animates, CTAs visible, nav transparent at top.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: add head, navigation, and hero section"
```

---

### Task 5: Build the HTML — Services Section

**Files:**
- Modify: `index.html` (add after hero section)

- [ ] **Step 1: Add the services section**

After the hero `</section>`, add `<section id="services">`:
- Container: `py-24 md:py-32 px-6 max-w-7xl mx-auto`
- Heading: `<h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] text-center mb-16" data-reveal="fade-up">What We Do</h2>`
- Grid: `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" data-stagger-parent>`
- 6 cards, each structured as:

```html
<div class="bg-surface rounded-lg p-8 border-l-4 border-primary hover:bg-elevated transition-colors duration-300" data-stagger-child data-tilt>
  <div class="text-primary text-4xl mb-4"><!-- SVG icon --></div>
  <h3 class="font-display text-2xl text-white uppercase tracking-[-0.03em] mb-3">Service Name</h3>
  <p class="text-text-secondary leading-[1.7]">Service description.</p>
</div>
```

Card content (with inline SVG icons — simple construction/building themed):

1. **Residential Scaffolding** — icon: house outline. "Safe, reliable scaffolding for home builds, extensions, loft conversions, and renovation projects of any size."
2. **Commercial Scaffolding** — icon: building outline. "Large-scale scaffolding solutions for commercial builds, industrial sites, and multi-storey projects across the UK."
3. **Safety Netting** — icon: shield/net outline. "Professional fall protection and safety netting systems installed to the highest standards for any height."
4. **Shrink Wrapping** — icon: wrap/cover outline. "Complete weather protection for roofing projects. Keep your site dry and your schedule on track."
5. **Permanent Handrails** — icon: rail/barrier outline. "Fixed handrail systems on tin sheet roofs for safe solar panel installation and ongoing roof access."
6. **Nationwide Coverage** — icon: map pin outline. "Based in Carlisle with teams covering the full UK. No job too far, no project too large."

- [ ] **Step 2: Screenshot and verify**

```bash
node screenshot.mjs http://localhost:3000 services
```

Check: 3x2 grid on desktop, 1-col on mobile, amber left borders, tilt hover effect, icons visible, text readable against dark cards.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add services section with 6 animated cards"
```

---

### Task 6: Build the HTML — About / Why Choose Us Section

**Files:**
- Modify: `index.html` (add after services section)

- [ ] **Step 1: Add the about section**

After services `</section>`, add `<section id="about">`:
- Container: `py-24 md:py-32 px-6 max-w-7xl mx-auto`
- Split layout: `<div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">`
  - Left (image): `<div class="lg:col-span-7"><img src="images/team-photo.jpg" alt="How High Scaffolding team" class="rounded-lg w-full object-cover shadow-2xl" loading="lazy" data-parallax="-80"></div>`
  - Right (text): `<div class="lg:col-span-5">`
    - Heading: `<h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] mb-8" data-reveal="fade-right">Why How High?</h2>`
    - 4 bullet points with amber icons:
      - Fully Insured — "Complete public and employer's liability coverage on every job."
      - CITB Certified — "All operatives hold current CITB cards and safety certifications."
      - Fast Turnaround — "Rapid response and efficient scaffold erection to keep your project on schedule."
      - UK-Wide Coverage — "Based in Carlisle, our teams operate across the entire United Kingdom."
    - Each bullet: `<div class="flex items-start gap-4 mb-6" data-reveal="fade-up">` with an amber checkmark/shield SVG icon and text.
    - Paragraph: `<p class="text-text-secondary leading-[1.7] mt-6" data-reveal="fade-up">"How High Scaffolding was built on doing the job right — safe, on time, every time. We take pride in every structure we erect, from a single residential scaffold to full commercial access solutions."</p>`

- [ ] **Step 2: Add the stats row**

Below the about grid, still inside the section:
```html
<div class="grid grid-cols-2 md:grid-cols-4 gap-8 mt-20 text-center" data-stagger-parent>
  <div data-stagger-child>
    <span class="font-display text-5xl text-primary" data-counter="500" data-counter-suffix="+">0</span>
    <p class="text-text-secondary mt-2 uppercase tracking-wider text-sm">Projects Completed</p>
  </div>
  <div data-stagger-child>
    <span class="font-display text-5xl text-primary" data-counter="15" data-counter-suffix="+">0</span>
    <p class="text-text-secondary mt-2 uppercase tracking-wider text-sm">Years Experience</p>
  </div>
  <div data-stagger-child>
    <span class="font-display text-5xl text-primary" data-counter="100" data-counter-suffix="%">0</span>
    <p class="text-text-secondary mt-2 uppercase tracking-wider text-sm">Safety Record</p>
  </div>
  <div data-stagger-child>
    <span class="font-display text-5xl text-white">UK</span>
    <p class="text-text-secondary mt-2 uppercase tracking-wider text-sm">Wide Coverage</p>
  </div>
</div>
```

Note: The 4th stat "UK-Wide" doesn't use `data-counter` since it's text, not a number. Display it as static white text.

- [ ] **Step 3: Screenshot and verify**

```bash
node screenshot.mjs http://localhost:3000 about
```

Check: image left with parallax, text right on desktop, stacks on mobile, counters animate on scroll, stats row aligned.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add about section with stats counters"
```

---

### Task 7: Build the HTML — Gallery Section

**Files:**
- Modify: `index.html` (add after about section)

- [ ] **Step 1: Add the gallery section**

After about `</section>`, add `<section id="gallery">`:
- Background: `bg-surface`
- Container: `py-24 md:py-32 px-6 max-w-7xl mx-auto`
- Heading: `<h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] text-center mb-6" data-reveal="fade-up">Our Work</h2>`
- Filter tabs: `<div class="flex flex-wrap justify-center gap-4 mb-12" data-reveal="fade-up">`
  - 4 buttons: All (active by default), Residential, Commercial, Specialist
  - Active style: `bg-primary text-base`, inactive: `border border-text-secondary text-text-secondary hover:border-primary hover:text-primary`
  - Each button has `data-filter="all|residential|commercial|specialist"` and an onclick handler

- [ ] **Step 2: Add the gallery grid**

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4" id="gallery-grid" data-stagger-parent>
```

8 gallery items, each:
```html
<div class="relative overflow-hidden rounded-lg cursor-pointer group" data-category="residential" data-stagger-child onclick="openLightbox(this)">
  <img src="images/gallery-1.jpg" alt="Residential scaffolding project" loading="lazy" class="w-full h-64 object-cover transform group-hover:scale-105 transition-transform duration-500">
  <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-4">
    <span class="text-white font-semibold">Residential Scaffolding</span>
  </div>
</div>
```

Assign categories: gallery-1,6 = residential; gallery-2,7,8 = commercial; gallery-3,4,5 = specialist.

- [ ] **Step 3: Add gallery filter JS and lightbox**

At the bottom of the file (before `</body>`), add inline `<script>`:

```javascript
// Gallery filter
document.querySelectorAll('[data-filter]').forEach(btn => {
  btn.addEventListener('click', () => {
    const filter = btn.dataset.filter;
    document.querySelectorAll('[data-filter]').forEach(b => {
      b.classList.remove('bg-primary', 'text-base', 'border-primary');
      b.classList.add('border-text-secondary', 'text-text-secondary');
    });
    btn.classList.add('bg-primary', 'text-base');
    btn.classList.remove('border-text-secondary', 'text-text-secondary');

    document.querySelectorAll('#gallery-grid > div').forEach(item => {
      if (filter === 'all' || item.dataset.category === filter) {
        item.style.display = '';
      } else {
        item.style.display = 'none';
      }
    });
  });
});

// Lightbox
function openLightbox(el) {
  const img = el.querySelector('img');
  const overlay = document.createElement('div');
  overlay.className = 'fixed inset-0 z-[100] bg-black/90 flex items-center justify-center p-8 cursor-pointer';
  overlay.onclick = () => overlay.remove();
  overlay.innerHTML = '<img src="' + img.src + '" class="max-w-full max-h-full rounded-lg shadow-2xl">';
  document.body.appendChild(overlay);
}
```

- [ ] **Step 4: Screenshot and verify**

```bash
node screenshot.mjs http://localhost:3000 gallery
```

Check: grid layout, images visible, filter tabs styled, hover overlay effect.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: add gallery section with filters and lightbox"
```

---

### Task 8: Build the HTML — Video Showcase Section

**Files:**
- Modify: `index.html` (add after gallery section)

- [ ] **Step 1: Add the video showcase section**

After gallery `</section>`, add:
```html
<section class="bg-footer py-24 md:py-32 px-6">
  <div class="max-w-5xl mx-auto text-center">
    <h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] mb-12" data-split="words">See Us In Action</h2>
    <div class="relative rounded-xl overflow-hidden shadow-2xl" data-reveal="zoom">
      <video id="showcase-video" class="w-full" poster="images/hero-bg.jpg" preload="none">
        <source src="videos/showcase-video.mp4" type="video/mp4">
      </video>
      <div id="video-play-btn" class="absolute inset-0 flex items-center justify-center cursor-pointer bg-black/40 hover:bg-black/30 transition-colors duration-300" onclick="playShowcase()">
        <div class="w-20 h-20 rounded-full bg-primary flex items-center justify-center shadow-lg shadow-primary/30">
          <svg class="w-8 h-8 text-white ml-1" fill="currentColor" viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>
        </div>
      </div>
    </div>
  </div>
</section>
```

- [ ] **Step 2: Add play handler JS**

In the inline script block (before `</body>`):
```javascript
function playShowcase() {
  const video = document.getElementById('showcase-video');
  const btn = document.getElementById('video-play-btn');
  video.play();
  btn.style.display = 'none';
  video.controls = true;
}
```

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add video showcase section with play overlay"
```

---

### Task 9: Build the HTML — Testimonials Section

**Files:**
- Modify: `index.html` (add after video showcase section)

- [ ] **Step 1: Add the testimonials section**

After video `</section>`, add:
```html
<section class="py-24 md:py-32 px-6">
  <div class="max-w-7xl mx-auto">
    <h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] text-center mb-16" data-reveal="fade-up">What Our Clients Say</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
```

3 testimonial cards:
```html
<div class="bg-surface rounded-lg p-8 border-t-4 border-primary" data-reveal="fade-up">
  <div class="flex gap-1 mb-4">
    <!-- 5 amber stars -->
    <svg class="w-5 h-5 text-primary" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
    <!-- repeat 4 more times -->
  </div>
  <p class="text-text-secondary leading-[1.7] mb-6 italic">"Quote text here."</p>
  <div>
    <p class="text-white font-semibold">Client Name</p>
    <p class="text-text-secondary text-sm">Location</p>
  </div>
</div>
```

Placeholder testimonials:
1. "How High did an incredible job on our home extension. The scaffolding was up in a day and the team were professional from start to finish. Couldn't recommend them enough." — James T., Carlisle
2. "We've used How High on multiple commercial projects now. Always on time, always safe, always competitive. They're our go-to scaffolding contractor." — Sarah M., Manchester
3. "Needed safety netting and shrink wrapping on a tricky roof job. How High handled it perfectly — nothing was too much trouble. Top quality work." — David R., Leeds

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "feat: add testimonials section with 3 placeholder reviews"
```

---

### Task 10: Build the HTML — Contact / Quote Form Section

**Files:**
- Modify: `index.html` (add after testimonials section)

- [ ] **Step 1: Add the contact section**

After testimonials `</section>`, add `<section id="contact">`:
- Background: `bg-[#111111]`
- Container: `py-24 md:py-32 px-6 max-w-7xl mx-auto`
- Heading: `<h2 class="font-display text-4xl md:text-5xl text-white uppercase tracking-[-0.03em] text-center mb-16" data-reveal="fade-up">Get a Free Quote</h2>`
- Split: `<div class="grid grid-cols-1 lg:grid-cols-2 gap-12">`

Left (form):
```html
<form id="quote-form" onsubmit="handleSubmit(event)" class="space-y-6">
  <div>
    <label class="block text-sm text-text-secondary uppercase tracking-wider mb-2" for="name">Name *</label>
    <input type="text" id="name" name="name" required class="w-full bg-surface border border-elevated rounded px-4 py-3 text-white focus:border-primary focus:outline-none transition-colors" placeholder="Your name">
  </div>
  <div>
    <label class="block text-sm text-text-secondary uppercase tracking-wider mb-2" for="phone">Phone *</label>
    <input type="tel" id="phone" name="phone" required class="w-full bg-surface border border-elevated rounded px-4 py-3 text-white focus:border-primary focus:outline-none transition-colors" placeholder="Your phone number">
  </div>
  <div>
    <label class="block text-sm text-text-secondary uppercase tracking-wider mb-2" for="email">Email</label>
    <input type="email" id="email" name="email" class="w-full bg-surface border border-elevated rounded px-4 py-3 text-white focus:border-primary focus:outline-none transition-colors" placeholder="Your email address">
  </div>
  <div>
    <label class="block text-sm text-text-secondary uppercase tracking-wider mb-2" for="service">Service Required *</label>
    <select id="service" name="service" required class="w-full bg-surface border border-elevated rounded px-4 py-3 text-white focus:border-primary focus:outline-none transition-colors">
      <option value="" disabled selected>Select a service</option>
      <option value="residential">Residential Scaffolding</option>
      <option value="commercial">Commercial Scaffolding</option>
      <option value="safety-netting">Safety Netting</option>
      <option value="shrink-wrapping">Shrink Wrapping</option>
      <option value="handrails">Permanent Handrails</option>
    </select>
  </div>
  <div>
    <label class="block text-sm text-text-secondary uppercase tracking-wider mb-2" for="details">Project Details</label>
    <textarea id="details" name="details" rows="4" class="w-full bg-surface border border-elevated rounded px-4 py-3 text-white focus:border-primary focus:outline-none transition-colors resize-none" placeholder="Tell us about your project..."></textarea>
  </div>
  <button type="submit" class="w-full bg-primary hover:bg-primary-hover text-base font-semibold uppercase tracking-widest py-4 rounded transition-colors duration-300" data-magnetic>Send Enquiry</button>
  <div id="form-success" class="hidden text-center py-4 text-primary font-semibold">Thank you! We'll be in touch shortly.</div>
</form>
```

Right (contact info):
```html
<div class="space-y-8">
  <div>
    <h3 class="font-display text-2xl text-white uppercase mb-4">Get In Touch</h3>
    <div class="space-y-4">
      <a href="tel:07944362960" class="flex items-center gap-3 text-text-secondary hover:text-primary transition-colors">
        <svg class="w-6 h-6 text-primary" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>
        07944 362 960
      </a>
      <p class="flex items-center gap-3 text-text-secondary">
        <svg class="w-6 h-6 text-primary" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
        Based in Carlisle — Covering the Full UK
      </p>
    </div>
  </div>
  <div class="rounded-lg overflow-hidden h-64 lg:h-80">
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d36645.24285377492!2d-2.9589!3d54.8925!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x487d1f5b3126f837%3A0x7fb31ef38a0d18f3!2sCarlisle!5e0!3m2!1sen!2suk!4v1" width="100%" height="100%" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
  </div>
</div>
```

- [ ] **Step 2: Add form handler JS**

In the inline script block:
```javascript
function handleSubmit(e) {
  e.preventDefault();
  const form = document.getElementById('quote-form');
  const success = document.getElementById('form-success');
  // For now, show success message. Wire up to backend later.
  form.querySelectorAll('input, select, textarea, button').forEach(el => el.style.display = 'none');
  success.classList.remove('hidden');
}
```

- [ ] **Step 3: Screenshot and verify**

```bash
node screenshot.mjs http://localhost:3000 contact
```

Check: form fields styled dark, labels visible, dropdown works, map loads, phone clickable, submit button amber.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add contact section with quote form and map"
```

---

### Task 11: Build the HTML — Footer

**Files:**
- Modify: `index.html` (add after contact section)

- [ ] **Step 1: Add the footer**

After contact `</section>`, before the scripts, add:
```html
<footer class="bg-footer py-12 px-6 border-t border-elevated">
  <div class="max-w-7xl mx-auto">
    <div class="flex flex-col md:flex-row items-center justify-between gap-8">
      <img src="brand_assets/logo.png" style="filter:invert(1)" alt="How High Scaffolding" class="h-12">
      <nav class="flex flex-wrap gap-6 text-sm text-text-secondary">
        <a href="#services" class="hover:text-primary transition-colors">Services</a>
        <a href="#about" class="hover:text-primary transition-colors">About</a>
        <a href="#gallery" class="hover:text-primary transition-colors">Gallery</a>
        <a href="#contact" class="hover:text-primary transition-colors">Contact</a>
      </nav>
      <a href="tel:07944362960" class="text-primary hover:text-primary-hover transition-colors font-semibold">07944 362 960</a>
    </div>
    <div class="mt-8 pt-8 border-t border-elevated flex flex-col md:flex-row items-center justify-between gap-4 text-sm text-text-secondary">
      <p>&copy; 2026 How High Scaffolding. All rights reserved.</p>
      <p>Built by <a href="#" class="text-primary hover:text-primary-hover transition-colors">AireyAI</a></p>
    </div>
  </div>
</footer>
```

- [ ] **Step 2: Add script tags before closing body**

Ensure the scripts are ordered correctly at the bottom:
```html
<!-- GSAP + ScrollTrigger -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<!-- AireyAI Animation Toolkit -->
<script src="animations.js"></script>
<!-- Inline JS (nav scroll, mobile menu, gallery filter, lightbox, video, form) -->
<script>
  // Nav scroll effect
  window.addEventListener('scroll', () => {
    document.querySelector('nav').classList.toggle('bg-base', window.scrollY > 50);
    document.querySelector('nav').classList.toggle('shadow-lg', window.scrollY > 50);
  });

  // Mobile menu toggle
  const hamburger = document.getElementById('hamburger');
  const mobileMenu = document.getElementById('mobile-menu');
  if (hamburger && mobileMenu) {
    hamburger.addEventListener('click', () => mobileMenu.classList.toggle('hidden'));
    mobileMenu.querySelectorAll('a').forEach(a => a.addEventListener('click', () => mobileMenu.classList.add('hidden')));
  }

  // Gallery filter
  document.querySelectorAll('[data-filter]').forEach(btn => {
    btn.addEventListener('click', () => {
      const filter = btn.dataset.filter;
      document.querySelectorAll('[data-filter]').forEach(b => {
        b.className = b.className.replace(/bg-primary|text-base/g, '').trim();
        b.classList.add('border', 'border-text-secondary', 'text-text-secondary');
      });
      btn.classList.remove('border', 'border-text-secondary', 'text-text-secondary');
      btn.classList.add('bg-primary', 'text-base');
      document.querySelectorAll('#gallery-grid > div').forEach(item => {
        item.style.display = (filter === 'all' || item.dataset.category === filter) ? '' : 'none';
      });
    });
  });

  // Lightbox
  function openLightbox(el) {
    const img = el.querySelector('img');
    const overlay = document.createElement('div');
    overlay.className = 'fixed inset-0 z-[100] bg-black/90 flex items-center justify-center p-8 cursor-pointer';
    overlay.onclick = () => overlay.remove();
    const clone = document.createElement('img');
    clone.src = img.src;
    clone.className = 'max-w-full max-h-full rounded-lg shadow-2xl';
    overlay.appendChild(clone);
    document.body.appendChild(overlay);
  }

  // Video showcase
  function playShowcase() {
    const video = document.getElementById('showcase-video');
    const btn = document.getElementById('video-play-btn');
    video.play();
    btn.style.display = 'none';
    video.controls = true;
  }

  // Form handler
  function handleSubmit(e) {
    e.preventDefault();
    const form = document.getElementById('quote-form');
    const success = document.getElementById('form-success');
    form.querySelectorAll('input, select, textarea, button').forEach(el => el.style.display = 'none');
    success.classList.remove('hidden');
  }
</script>
```

- [ ] **Step 3: Full-page screenshot and review**

```bash
node screenshot.mjs http://localhost:3000 full-page
```

Review the full page top to bottom: nav, hero, services, about, gallery, video, testimonials, contact, footer. Check all sections are present, spacing consistent, animations wired up.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add footer and consolidate all inline scripts"
```

---

### Task 12: Browser Testing with Playwright

**Files:** None modified — testing only.

- [ ] **Step 1: Open site in Playwright and test navigation**

Using Playwright MCP tools:
- Navigate to `http://localhost:3000`
- Verify page loads, title correct
- Click each nav link (Services, About, Gallery, Contact) — verify smooth scroll to correct section
- Click "Get a Quote" button — verify scrolls to contact form

- [ ] **Step 2: Test interactive elements**

- Click gallery filter tabs (Residential, Commercial, Specialist, All) — verify filtering works
- Click a gallery image — verify lightbox opens
- Click lightbox overlay — verify it closes
- Click video play button — verify video starts
- Fill in the quote form with test data and submit — verify success message appears

- [ ] **Step 3: Test mobile layout**

- Resize browser to 375px width
- Verify hamburger menu appears and works
- Verify all sections stack vertically
- Verify touch targets are at least 44px
- Verify no horizontal overflow

- [ ] **Step 4: Test click-to-call**

- Verify `tel:07944362960` links are present in nav, hero, and contact section

---

### Task 13: Lighthouse Audit

- [ ] **Step 1: Run Lighthouse audit**

Use the Lighthouse MCP tools to audit `http://localhost:3000`:
- `mcp__lighthouse__get_performance_score`
- `mcp__lighthouse__get_accessibility_score`
- `mcp__lighthouse__get_seo_analysis`
- `mcp__lighthouse__get_core_web_vitals`

- [ ] **Step 2: Fix any issues flagged**

Address any scores below 90. Common fixes:
- Add missing `alt` attributes
- Ensure color contrast passes
- Add `width` and `height` to images to prevent layout shift
- Ensure font loading doesn't block render

- [ ] **Step 3: Re-audit and confirm passing**

Run Lighthouse again after fixes. All scores should be 90+.

- [ ] **Step 4: Commit any fixes**

```bash
git add index.html
git commit -m "fix: address Lighthouse audit findings"
```

---

### Task 14: Final Screenshot Comparison and Polish

- [ ] **Step 1: Full desktop screenshot**

```bash
node screenshot.mjs http://localhost:3000 final-desktop
```

Review every section for: spacing consistency, font rendering, color accuracy, animation data attributes present, no broken images.

- [ ] **Step 2: Mobile screenshot (resize viewport)**

Take a mobile-width screenshot and review: stacking, text size, touch targets, nav hamburger.

- [ ] **Step 3: Fix any visual issues found**

Address anything that looks off — spacing, alignment, color mismatches.

- [ ] **Step 4: Final commit**

```bash
git add -A
git commit -m "polish: final visual adjustments after screenshot review"
```
