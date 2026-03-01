---
name: landing-page-builder
description: Builds complete, high-converting landing pages from scratch. Use this skill when the user asks to create a landing page, sales page, opt-in page, product page, or any single-goal conversion-focused web page. Covers structure, copywriting, UI, responsiveness, and SEO.
---

# Landing Page Builder Skill

This skill guides the agent through building a complete, high-converting landing page
with proper structure, persuasive copy, clean UI, and technical best practices.

## When to use this skill

- User asks to create a landing page, sales page, or opt-in page
- User wants to promote a product, service, event, or lead magnet
- User needs a focused conversion page (single CTA goal)
- User provides a brief and wants a full page generated

---

## Phase 1 – Discovery (Ask Before Building)

Before generating any code, collect the following information. If the user hasn't
provided it, ask in a single grouped message:

1. **Product/Service name** – What is being promoted?
2. **Target audience** – Who is this page for?
3. **Primary goal / CTA** – What action should visitors take? (e.g., sign up, buy, download)
4. **Key benefits** – What are the top 3–5 benefits or differentiators?
5. **Social proof available?** – Testimonials, logos, reviews, stats?
6. **Visual style preference** – Minimalist, bold, corporate, playful?
7. **Color palette / brand** – Primary colors or brand identity?
8. **Tech stack** – Plain HTML/CSS/JS, React, Next.js, Vue, Tailwind, etc.?

If the user provides a brief with enough context, skip to Phase 2.

---

## Phase 2 – Page Structure

Always build the landing page following this section order:

### 1. `<head>` – SEO & Meta
- Title tag: benefit-driven, under 60 characters
- Meta description: compelling, ~155 characters, includes the primary keyword
- Open Graph tags for social sharing
- Viewport meta for mobile responsiveness
- Link to stylesheet / import fonts

### 2. Hero Section (`#hero`)
The most critical section — above the fold.
- **Headline**: benefit-first, clear value proposition, max 10 words
- **Subheadline**: expands on the headline, addresses the core pain point (1–2 sentences)
- **Hero visual**: image or video relevant to the offer
- **Primary CTA button**: action-oriented text (e.g., "Get Free Access", "Start Today")
- Remove navigation links — no distractions allowed

### 3. Problem Section (`#problem`)
- Acknowledge the visitor's pain point or challenge
- Use empathetic, relatable language
- Short paragraphs or 3-icon layout

### 4. Solution Section (`#solution`)
- Present the product/service as the answer
- Highlight the top 3–5 benefits (not just features)
- Use icons + short benefit headlines + one-sentence descriptions

### 5. How It Works (`#how-it-works`)
- 3-step numbered process (keep it simple)
- Reassure the visitor that getting started is easy

### 6. Social Proof (`#proof`)
- Testimonials with name, photo, and role/company
- Trust badges (logos of clients, press mentions, security seals)
- Stats or numbers (e.g., "10,000+ happy customers")

### 7. Offer / Pricing (`#offer`) *(if applicable)*
- Clear pricing tiers or offer details
- Highlight the recommended plan
- Include a guarantee or risk-reversal statement (e.g., "30-day money-back guarantee")

### 8. FAQ (`#faq`)
- Answer the top 5–7 objections or common questions
- Use accordion/collapsible format for UX

### 9. Final CTA Section (`#cta-final`)
- Repeat the primary CTA
- Reinforce the main benefit in 1 headline
- Urgency or scarcity element if applicable (e.g., "Limited spots available")

### 10. Footer (`#footer`)
- Copyright notice
- Privacy Policy and Terms of Service links
- Social media links (optional)
- Contact information

---

## Phase 3 – Copywriting Rules

Follow these copy principles throughout the page:

- **Benefit over feature**: "Save 3 hours a day" not "Has automation tools"
- **Second person**: Use "you" and "your" to speak directly to the reader
- **Active voice**: "Get instant access" not "Instant access can be obtained"
- **Scannable**: Short paragraphs (2–3 lines max), bullet points, bold key phrases
- **One CTA only**: Never mix multiple goals — all CTAs must lead to the same action
- **Headline formula options**:
  - `[Result] without [pain point]`
  - `The [adjective] way to [desired outcome]`
  - `Finally, [solve problem] in [timeframe]`

---

## Phase 4 – UI & Design Rules

### Layout
- Single-column layout preferred for focus
- Z-pattern or F-pattern visual hierarchy
- Ample white space between sections (min 80px padding per section)
- Sticky CTA bar or button for long-scroll pages

### Typography
- Max 2 font families (one for headings, one for body)
- Hero headline: 48–72px
- Section headings: 28–36px
- Body text: 16–18px, line-height 1.6
- High contrast between text and background (WCAG AA minimum)

### Color
- Use the provided brand palette
- If no palette given, default to: one strong primary, one neutral background, one accent for CTA
- CTA button must stand out — use the highest-contrast color on the page

### Imagery
- Hero image must be relevant and high quality (≥1200px wide)
- Use real people/photos when possible (more trust than illustrations)
- Compress all images for performance (WebP format preferred)

### Responsiveness
- Mobile-first approach
- Stack all multi-column sections vertically on screens < 768px
- CTA button must be full-width on mobile
- Tap targets minimum 44x44px

---

## Phase 5 – Technical Best Practices

### Performance
- Lazy load images below the fold
- Minify CSS and JS
- Preload hero image and critical fonts
- Target Lighthouse Performance score ≥ 90

### Accessibility
- Semantic HTML (`<header>`, `<main>`, `<section>`, `<footer>`)
- All images must have descriptive `alt` attributes
- Form labels associated with inputs
- Keyboard-navigable interactive elements
- Sufficient color contrast ratio (4.5:1 for body text)

### Forms (if applicable)
- Minimize fields — ask only what is essential
- Inline validation with clear error messages
- Submit button copy must reinforce the CTA (e.g., "Send My Free Guide")
- Add a micro-copy line below the button (e.g., "No spam. Unsubscribe anytime.")

### Analytics & Tracking
- Include a placeholder or snippet for Google Analytics / GTM
- Add conversion event tracking to the CTA button
- Set up Facebook Pixel placeholder if the user mentions ads

---

## Phase 6 – Output Format

Deliver the final output as:

1. **Full source code** in the requested tech stack
2. **File structure** if it's a multi-file project:

landing-page/
├── index.html
├── styles/
│ └── main.css
├── scripts/
│ └── main.js
└── assets/
└── images/

3. **Short summary** of decisions made (color palette, fonts used, CTA chosen)
4. **Next steps suggestion**: A/B test ideas, integrations, or content to improve

---

## Decision Tree

User request received
│
├── Has enough info? ──No──► Ask Phase 1 questions
│
└── Yes
│
├── Tech stack specified? ──No──► Default to HTML + Tailwind CSS
│
├── Build all 10 sections in order (Phase 2)
├── Apply copywriting rules (Phase 3)
├── Apply UI/design rules (Phase 4)
├── Apply technical best practices (Phase 5)
│
└── Deliver full output (Phase 6)


---

## Example Headline Variations

| Niche        | Headline Example                                      |
|--------------|-------------------------------------------------------|
| SaaS         | "Automate your reports in 5 minutes — no code needed" |
| E-commerce   | "Finally, skincare that actually works for dark skin" |
| Online course| "Go from zero to job-ready in 60 days"               |
| Agency       | "We build landing pages that double your conversions" |
| App          | "Your finances, organized — in under 2 minutes"      |
