# Kylex Landing Page — Build Instructions

> Kylex Suite (kylex.io)
> Titania Labs LLC — Confidential
> Version: v1.0

---

## What you are building

A marketing landing page for Lodestar (Kylex Module 00) that introduces the product, communicates value, surfaces tier differentiation, and converts visitors to either a free CLI download or Kylex Pro early access sign-up.

**Lodestar** is a CLI + MCP tool that captures coding session context and synthesizes portable `.lodestar.md` artifacts for warm cold-starts. Free forever.

**Kylex Pro** is the upsell tier (subscription, pricing TBD) with cross-device sync, suite integration, and priority support.

---

## Decisions — locked

| Decision | Answer |
|---|---|
| Email capture strategy | Option B — ungated download, email required only for Pro early access |
| Domain | kylex.io |
| Email platform | Beehiiv ($0 up to 2,500 subs, API for triggered emails) |
| Framework | Astro (static site, fast, single page) |
| Pro pricing | "Early Access" — no price published at launch |
| Brand | Ship with current placeholder logo, full brand pass later |
| CLI distribution | Ungated — direct download link, npm, Homebrew. No email gate. |

---

## Tech stack

| Layer | Choice | Notes |
|---|---|---|
| Framework | Astro | Static site, SSR not needed for single page |
| Styling | Tailwind CSS | Matches Kylex design posture |
| Hosting | Vercel | Static deploy, SSL, CDN |
| Email | Beehiiv API | Triggered welcome email on Pro sign-up |
| Analytics | Minimal first-party | Page views, CTA clicks only. No third-party pixels. |
| CI/CD | GitHub Actions | Deploy from main branch |
| Domain | kylex.io | |

---

## Page architecture

### Section 1 — Hero
- Lodestar wordmark + Kylex suite badge
- Headline: communicates session amnesia problem + solution
- Sub-headline: "Every session remembers where you left off."
- Primary CTA: Download Lodestar Free (direct link, no email gate)
- Secondary CTA: Join Kylex Pro Early Access

### Section 2 — Problem statement
- "Every AI coding session starts cold" — the pain
- Visual: before/after or session flow diagram

### Section 3 — How it works
- Three steps: `lodestar start` → code → `lodestar end`
- Terminal-style mockup or animation
- Emphasize simplicity: three commands, that's it

### Section 4 — What .lodestar.md looks like
- Real example output (decisions, patterns, rejected approaches)
- "Not a git log. A handoff note from a thoughtful colleague."

### Section 5 — Tier comparison
- Lodestar Free vs Kylex Pro table
- Free: session capture, .md synthesis, warm starts, local drift detection
- Pro: cross-device sync, suite integration (Kite, Gangway, Pharos), priority support
- Pro CTA: "Join Early Access — founding member rate"

### Section 6 — Download / Install
- Three install methods: binary download, npm, Homebrew
- No email gate — direct links
- Optional inline: "Stay updated on releases" email field (pre-unchecked)

### Section 7 — Pro Early Access
- Email required to join early access
- Newsletter opt-in checkbox (pre-unchecked, separate consent)
- Privacy promise: "Your email is used for Lodestar updates only. Never sold."
- CTA: "Join Kylex Pro Early Access — be first to know pricing"

### Section 8 — Footer
- Kylex suite links (placeholder for future products)
- Legal: Privacy Policy, Terms
- Newsletter sign-up (compact)
- "Built by Titania Labs LLC"

---

## Target personas

### Primary: The Vibe-Coding Developer
- Uses Cursor, Lovable, Bolt.new, Claude Code, or Replit
- Ships solo or on small teams (1–5 eng)
- Loses context between AI sessions
- Evaluates tools by: GitHub stars, README quality, zero-friction install
- Email gate tolerance: very low

### Secondary: The AI-Curious Technical Lead
- Evaluates tools for team adoption
- Needs to understand value before recommending
- Cares about: security posture, data locality, integration surface

---

## Email capture — functional requirements

### Surface 1 — Download CTA (ungated)
- Download button is direct — no email required
- Below button: optional inline email field + newsletter opt-in checkbox
- Checkbox pre-unchecked
- Copy: "Stay updated on Lodestar releases — optional. No spam, ever."

### Surface 2 — Pro Early Access CTA (required)
- Email required to join early access list
- Newsletter opt-in checkbox (pre-unchecked, separate from access)
- Privacy promise displayed inline

### Surface 3 — Footer newsletter
- Compact standalone form
- Email field + checkbox
- Copy: "Get Lodestar release notes and Kylex suite updates."
- Pre-unchecked

### All surfaces
- Pre-unchecked checkboxes on ALL surfaces (CAN-SPAM compliance)
- On submit: inline confirmation, no page navigation
- Duplicate handling: silent dedup
- Segmentation: Free download intent, Newsletter subscribers, Pro early access intent
- One-click unsubscribe in every email
- No third-party tracking pixels

---

## Brand tokens

| Token | Value |
|---|---|
| Primary mark color | #185FA5 |
| Wordmark color | #0C447C |
| Dark bg treatment | White mark on #0C447C |
| Light bg treatment | #185FA5 mark on #E6F1FB |
| Mark shape | Asymmetric Polaris star |
| Status | Placeholder — full brand pass required pre-launch |

---

## Performance requirements

- LCP < 2s
- CLS < 0.1
- FID < 100ms
- Mobile responsive: 375px, 768px, 1280px
- WCAG 2.1 AA accessibility minimum
- Works without JavaScript (progressive enhancement)

---

## Out of scope

- Full Kylex suite landing pages (Kite, Gangway, Pharos)
- Blog, changelog, documentation site
- User dashboard or account portal
- Payment processing
- CLI distribution infrastructure (npm, Homebrew publishing)
- Full brand identity system

---

## Coding conventions

- Astro components in `src/components/`
- Tailwind for all styling — no custom CSS files
- Semantic HTML throughout
- All images optimized (WebP, lazy load)
- No third-party scripts except Beehiiv form embed
- Accessible: alt text, ARIA labels, keyboard navigation

---

## Build and run

```bash
npm install
npm run dev          # local dev server
npm run build        # production build
npm run preview      # preview production build
```

---

*Kylex Landing Page — Titania Labs LLC*
*kylex.io*
