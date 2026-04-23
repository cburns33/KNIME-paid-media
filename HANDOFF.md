# KNIME Paid Media Manager Interview — Project Handoff

## What this is

A **2-exercise interview assessment** for a Paid Media Manager position at KNIME. Demonstrates paid media strategy, audience targeting, budget allocation, and creative execution for B2B enterprise SaaS.

**Exercise 1**: Reveal.js presentation (10 slides) with GSAP animations
**Exercise 2**: Styled HTML campaign assessment report (print-optimized for PDF)

Both deployed to Netlify via GitHub auto-deploy.

## Project location

```
C:\Users\chase\OneDrive\Documents\Claude Code Projects\knime-presentation\
├── KNIME-paid-media-plan.html     ← Exercise 1: Reveal.js presentation
├── knime-campaign-assessment.html ← Exercise 2: Assessment report
├── KNIME Mock Campaign Assessment.md ← Source markdown for Ex 2
├── netlify.toml                   ← Deployment config + redirects
├── .gitignore                     ← Git exclusions
├── HANDOFF.md                     ← This file
└── assets\
    ├── KNIMELogoTM.svg            ← Logo (inverts on dark slides via CSS filter)
    ├── Figtree-VariableFont_wght.ttf ← Headings
    ├── Figtree-Italic-VariableFont_wght.ttf
    ├── Inter-Regular.ttf          ← Body
    └── Inter-Italic.ttf
```

Open `KNIME-paid-media-plan.html` directly in Chrome. No build step. Reveal.js from jsDelivr CDN (v5). Fonts load locally via `@font-face`.

## Keyboard

| Key | Action |
|---|---|
| ← / → / Space | Navigate |
| S | Open speaker view (shows notes + next slide + timer) |
| F | Fullscreen |
| Esc | Overview mode |
| `?print-pdf` appended to URL | Print-friendly PDF export view |

## Brand tokens (defined as CSS variables at top of `<style>`)

```
--knime-yellow: #FFDE00
--knime-orange: #F89639
--knime-mint:   #A8D5C2   (observed in active KNIME ad creative)
--charcoal:     #231F20
--charcoal-2:   #2d2829   (card backgrounds on dark slides)
--light-gray:   #F2F2F2
--white:        #FFFFFF
--muted:        #6B7280
--muted-dark:   #9aa0a6   (muted text on dark backgrounds)
```

Typography:
- **Figtree** — headings, eyebrows, stat values, card labels
- **Inter** — body, lists, paragraphs
- No Google Fonts CDN. All fonts loaded locally via `@font-face` with `format('truetype-variations')`.

## Slide inventory (Exercise 1)

| # | Title | Background | Accent | Key component |
|---|---|---|---|---|
| 1 | Title | Dark charcoal | Yellow ripple animation | Name, date, circular ripple pattern, fragment-triggered |
| 2 | Program Assumptions | Dark charcoal | Yellow | 4 stat boxes + 6-item two-column assumptions list |
| 3 | Persona 01 — Technical Champion | Light gray | Mint `#A8D5C2` | 2×2 persona card grid + targeting assumption callout |
| 4 | Persona 02 — Operations VP | Light gray | Orange `#F89639` | 2×2 persona card grid + targeting logic callout |
| 5 | Persona 03 — Enterprise Architect | Light gray | Yellow `#FFDE00` | 2×2 persona card grid + credential note callout |
| 6 | Persona 04 — Economic Buyer | Dark charcoal | Mint `#A8D5C2` | 2×2 persona card grid + credential note callout |
| 7 | Engagement Model | Dark charcoal | Mint / Orange / Yellow per phase | 3-column Concentric Circle rollout, fragments reveal L→R |
| 8 | Channel & Budget | Light gray | LinkedIn Orange / Search Yellow / Contextual Mint / Retargeting Gray | Budget bars + keyword clusters + LinkedIn progression graphic |
| 9 | Metrics & Measurement | Dark charcoal | Mint / Orange / Yellow per tier | 4 animated stat counters + 3 tier columns (fragments) + Excluded + Reporting boxes |
| 10 | Closing | Dark charcoal | Yellow | Contact info, call to action |

## Reusable CSS components

- `.stat-box` — large numeric + label (Slides 1, 7)
- `.tier-column` — accent top-bar + numbered label + list with `<strong>` headers (Slides 5, 7)
- `.persona-card` — 2×2 grid card with muted header label (Slides 2, 3, 4)
- `.callout` — yellow / accent-colored panel for assumptions, targeting logic, credentials
- `.logo-mark` — top-right KNIME logo, white-inverted via `filter: brightness(0) invert(1)` on dark slides
- `.corner-stack` — decorative rotated rectangles bottom-left (yellow / orange / mint), pure CSS, no images
- `.budget-row` — horizontal bar chart row used on Slide 6
- `.keyword-cluster` — 3-card cluster for Branded / Category / Competitive search buckets
- `.kap-bg` — Slide 5 background image panel with linear-gradient mask
- `.accent-bar` — 5px top stripe on persona slides

## Animations

- **Slide 7 counter animation:** runs via `requestAnimationFrame` on `slidechanged` event when the metrics slide becomes current. Ease-out cubic, ~1.1s duration. Data-attributes `data-counter`, `data-prefix`, `data-suffix` on each `.stat-value`. Also re-triggers on initial page load if user deep-links to Slide 7.
- **Reveal fragments:** `.fragment.fade-up` on tier columns in Slides 5 and 7 (left-to-right reveal), and on the Excluded / Stakeholder Reporting boxes on Slide 7.
- No decorative animation elsewhere. Fragments are used only where they reinforce read order.

## Writing-style rules (applied throughout this deck)

Per Chase's global Claude rules. Enforce these on any future edits:

1. **No em dashes.** Use comma, period, colon, or rewrite. Already applied to all headlines, subtitles, body copy, card text, callouts, and speaker notes.
2. **No correlative negation / antithesis framing.** Avoid "not X, but Y" and "it's not just X; it's Y."
3. **Minimal adverbs.** Let nouns and verbs carry the weight.

Note: `"Building a pipeline engine. Not an MQL factory."` on Slide 1 is Chase's own authored tagline and was kept intentionally as two sentences rather than rewritten.

## Content provenance

All on-slide copy and speaker notes come from Chase's kickoff prompt verbatim, with only these transformations:

- Em dashes replaced (per rule above)
- Quote characters converted to curly quotes (`&ldquo;` / `&rdquo;`) for visual polish
- Lists in paragraph-style card bodies were kept as prose (not converted to bullets) to respect the card density

No content was invented, reordered, or editorialized. If future edits touch copy, preserve Chase's voice and specific proof points:

- Siemens 90% reporting time reduction (Persona 2)
- Infineon self-serve (Persona 2)
- Audi €30K/year saved, 80% debugging cost reduction (Persona 3)
- Volkswagen 500+ hours reclaimed (Persona 3)
- Sasha Rezvina, VP Marketing, authored "What's Keeping AI Off the Factory Floor?" (Persona 2)
- "Pilot purgatory" is KNIME's own language from their blog (Persona 3)
- IFS background as credential (Persona 4)
- Active "From Alteryx to KNIME" LinkedIn campaigns that Chase spotted in the wild (Persona 4)

## Math anchors (for verbal delivery)

- $15M pipeline ÷ ~$100K ACV = 150 customers needed
- 150 SALs at 15% SAL rate = ~1,000 qualified leads required
- $50K/mo × 12 = $600K annual spend
- $600K ÷ 1,000 leads = **$600 CPL target**
- $600K ÷ 150 SALs = **$4,000 CPA/SAL ceiling**

These numbers are baked into Slide 1 and echoed on Slide 7 stat counters ($4K CPA, $15M pipeline, 15% SAL rate, 60% ICP match rate).

## Deployment

| Item | URL |
|------|-----|
| GitHub Repo | https://github.com/cburns33/KNIME-paid-media.git |
| Live Presentation | https://knime-paid-media.netlify.app |
| Live Assessment | https://knime-paid-media.netlify.app/assessment |

**Config**: `netlify.toml` sets up redirects:
- `/` → `/KNIME-paid-media-plan.html`
- `/assessment` → `/knime-campaign-assessment.html`

Auto-deploys on push to `main` branch.

## Exercise 2: Campaign Assessment (`knime-campaign-assessment.html`)

**Purpose**: Mock campaign assessment based on provided performance data

**Format**: Standalone HTML with dark theme, print-optimized for PDF export

**Sections**:
1. Data Gaps & Assumptions (card-based layout with bullet icons)
2. Performance Takeaways (channel cards with colored bullets, centered lead callout)
3. Action Items:
   - Quick Wins (yellow accent, box #4 filled)
   - 30-Day Projects (orange accent, box #2 filled)
   - Tests to Consider (mint accent, box #3 filled)
4. Communication Strategy (Marketing/Sales comms cards)

**Key Features**:
- KNIME brand colors (yellow `#FFDE00`, orange `#F89639`, mint `#A8D5C2`, charcoal `#231F20`)
- Custom fonts (Figtree, Inter) loaded locally
- Badge-style numbered cards with accent fills on specific items
- Triangle bullet icons on paragraph text
- Print media query CSS for clean PDF export

**How to use**: Open in browser, Ctrl+P, save as PDF. Dark theme preserved in print.

## Reveal.js config

```js
new Reveal({
  width: 1440, height: 900, margin: 0.04,
  minScale: 0.2, maxScale: 2.0,
  hash: true, controls: true, progress: true,
  slideNumber: false,
  transition: 'slide', backgroundTransition: 'fade',
  plugins: [ RevealNotes ],
})
```

The 1440×900 virtual canvas gives enough horizontal room for the 2×2 persona grids and the 4-column stat rows. Reveal auto-scales to the viewport.

## Strategic Concepts Demonstrated

1. **Concentric Circle Engagement Model**
   - Circle 1: CRM matched lists (warm)
   - Circle 2: TAL expansion + lookalikes
   - Circle 3: Title/industry cold with persona variants

2. **SAL-First Philosophy**
   - MQLs as leading indicators, SALs as north star
   - Quality over volume in targeting

3. **Persona-Based Targeting**
   - Technical Champion (search-heavy)
   - Operations VP (cost-pressured, championed)
   - Enterprise Architect (IT decision-maker)
   - Economic Buyer (deal escalator)

4. **Budget Allocation**
   - LinkedIn ABM: $22K (44%)
   - Google Search: $15K (30%)
   - Contextual/Trade: $8K (16%)
   - Retargeting: $5K (10%)

5. **Display Philosophy**
   - No GDN (junk inventory)
   - Whitelisted contextual only (IndustryWeek, Manufacturing.net, KNIME Community Forum)

## How This Fits Your Consultancy Portfolio

**Use Case**: This demonstrates end-to-end paid media strategy + execution — from audience segmentation and budget modeling to client-facing presentation and assessment deliverables.

**Reusable Patterns**:
- **Persona-based targeting framework** — adaptable to any B2B SaaS
- **Concentric Circle rollout** — warm-to-cold acquisition playbook
- **Badge-card content design** — assessment/action item formatting
- **Dark brand theme with accent colors** — consistent visual identity

**Technical Assets**:
- Reveal.js presentation template with GSAP animations
- Print-optimized HTML report template
- Netlify + GitHub auto-deploy setup
- Custom CSS variable-based design system

**Positioning**: This could be positioned as a case study for "B2B SaaS Paid Media Strategy" or "Enterprise Tech Audience Segmentation" on your consultancy site. The KNIME brand is recognizable in the data science space.

## Notes for Future Work

- **GSAP animations** are slide-index based (`h` parameter) — adding/removing slides requires updating the `buildTimeline()` function in the JS block
- **Speaker notes** are formatted as HTML `<ul>` lists for proper rendering
- **Fonts** load locally — if hosting elsewhere, ensure Figtree/Inter are accessible
- The title slide animations are **fragment-triggered** (arrow click) so they play when you actually start presenting
- The **LinkedIn progression graphic** on Slide 8 is a custom flexbox component, not an image

## How to Continue in Windsurf

1. Open `C:\Users\chase\OneDrive\Documents\Claude Code Projects\knime-presentation\` in Windsurf
2. **Presentation**: Edit `KNIME-paid-media-plan.html`. CSS in `<style>` block at top, JS in `<script>` block at bottom. Slides are `<section>` children of `.slides` in document order (0–9)
3. **Assessment**: Edit `knime-campaign-assessment.html` for Exercise 2 changes
4. Test by opening files directly in Chrome (no dev server required)
5. To deploy: `git add . && git commit -m "message" && git push` — Netlify auto-deploys

## Project Status

Submitted to KNIME for Paid Media Manager interview on April 21, 2026. All deliverables complete and deployed.
