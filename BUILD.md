# Ramp/Jet — Web Build Reference

> Onboarding doc for the Ramp/Jet landing page. Read this first if you're picking up the project in a new chat.

---

## What it is

A single-file marketing site for **Ramp/Jet**, a B2B mid-market service that rebuilds clients' websites into self-improving growth engines — engineered for discovery across both AI search (ChatGPT, Perplexity, Gemini, Google AI Overviews) and traditional Google. The product is positioned as a **continuous loop / system**, not a 90-day project.

**Brand vocabulary:**
- Tier names: **Ramp** (Configure / Foundation), **Calibrate/Tune** (Optimize), **Jet** (Accelerate)
- Phase verbs: Configure → Optimize → Accelerate
- Brand mark uses an orange `/` separator (styled via `.slash` class)

---

## File layout

```
~/Desktop/RampJetHomePage/
├── rampjet.html        ← the entire site (one self-contained file)
└── BUILD.md            ← this file
```

There is **no build step**. No bundler, no framework. Vanilla HTML + inline `<style>` + a small inline `<script>` for the rotating headline word.

---

## Local dev

```bash
cd ~/Desktop/RampJetHomePage
python3 -m http.server 8000
# Open http://localhost:8000/rampjet.html
```

(Static file — any HTTP server works. `python3 -m http.server` is fine.)

---

## Core positioning (the through-line)

Five sentences that **must land** in the order they appear in the page:

1. **Hero subhead** — *"We turn your website into a self-improving growth engine — engineered for discovery across AI search and Google, structured for conversion, and continuously refined based on real visitor behavior."*
2. **Problem section headline** — *"Search is mission critical. Now it's changing. Most companies have no idea."*
3. **How It Works title** — *"Three phases. One continuous loop."*
4. **Approach intro** — *"Our flywheel is the magic."* (bolded) and *"Most agencies sell you a project. We run you a system."*
5. **Approach point 01** — *"A flywheel, not a one-time project"*

If those five sentences are present and prominent, the positioning is intact. Don't break them without a strong reason.

---

## Voice & tone (apply throughout)

- **Confident but not bombastic** — describe a system, not promises
- **Engineering-flavored** — *engineered, calibrated, tuned, refined, signal* belong; *boost, supercharge, unlock, dominate* do not
- **Cyclical not linear** — *each cycle, continuously, the next round, every rotation* over *delivers, produces, results in*
- **Specific not generic** — name actual platforms (ChatGPT, Perplexity, Gemini), actual mechanics (citation, attribution, ICP fit)

**Words to favor:** loop, cycle, calibrate, refine, signal, compound, altitude, engineered, citation, surface area, pipeline.

**Words to avoid:** boost, scale (as a verb), unlock, supercharge, accelerate (overused), dominate, crush, leverage (as a verb), synergy, holistic.

---

## Page sections (top to bottom)

### 1. Hero
- **Eyebrow:** "For mid-market B2B teams"
- **H1:** "Be the answer when buyers ask `[ChatGPT / Google / Perplexity / Bing / Gemini / Claude / Copilot / DuckDuckGo]`" — the bracketed word rotates via small JS at the bottom of the file. The rotator uses an invisible **sizer span** (longest word, "DuckDuckGo") to prevent layout shift.
- **Subhead:** see "Core positioning" above.
- **CTAs:** primary "Get your AI visibility baseline" → `#contact`; secondary "See how it works" → `#how`.
- **Hero animation** — the giant SVG flywheel on the right. *Detailed below*.

### 2. Proof band (scrolling marquee)
Five tiles, doubled for seamless loop:
- 96% of pages get zero Google traffic
- AI search up 527% YoY
- 89% of B2B buyers use AI search
- 5x conversion vs. traditional organic
- Only 11% of domains cited by both ChatGPT & Perplexity

### 3. Problem / "The Shift" (dark section)
- **Eyebrow:** "The shift"
- **Headline:** *"Search is mission critical. / Now it's changing. / **Most companies have no idea.***" (third line italic accent)
- **Body:** opens with the 96% kicker, ends with *"You need a system. You need Ramp/Jet."*
- **4 stats** (in this order, mirroring the body's narrative arc):
  1. **96%** — Of web pages get zero traffic from Google — most companies haven't even won legacy search
  2. **527%** — YoY growth in AI-referred web sessions
  3. **5×** — Higher conversion rate from AI search vs. traditional organic
  4. **89%** — Of B2B buyers now use AI search throughout the buying process
- **Sources line:** *Sources: Previsible (2025), Exposure Ninja (2026), Forrester Buyers' Journey Survey (2024), Ahrefs (2023).*

### 4. How It Works
- **Title:** "Three phases. *One continuous loop.*"
- **Intro:** *"We don't run a 90-day project and disappear. Ramp, Calibrate/Tune, Jet — then we re-run the process with a higher performance baseline. Each cycle compounds on the last, and your growth keeps pace with the way buyers actually search."*
- **Three tier cards** (with SVG icons replacing the original R/C/J letters):
  - **PHASE 01 / Configure** — `Ramp` — tagline *"Get the house in order."* Icon: ramp wedge with filled corner accent.
  - **PHASE 02 / Optimize** — `Calibrate/Tune` — tagline *"Refine the system."* Icon: speedometer / gauge with needle.
  - **PHASE 03 / Accelerate** — `Jet` — tagline *"Turn traffic into pipeline."* Icon: rocket with body / window / fins.
- The slash in `Calibrate/Tune` uses `<span class="slash">/</span>` — same orange treatment as the logo.

### 5. Pull quote
> *"We don't optimize for rankings. We engineer a system that gets continuously smarter — every cycle, your business shows up sharper, in more places, in front of better buyers."*

`continuously smarter` is the accent-color phrase.

### 6. Approach / "Built for how visibility actually works"
- **Title:** "Built for how *visibility actually works.*"
- **Intro paragraph** opens with bolded *"Our flywheel is the magic."* and ends with *"Most agencies sell you a project. We run you a system."*
- **Four points:**
  1. **A flywheel, not a one-time project** — *"Could you use Ramp/Jet for one cycle and call it quits? Sure — and you'd achieve measurably better visibility. 90 days later you'll need a refresh. Each cycle compounds on the last, elevating your visibility and pipeline in the current context of search and discovery."*
  2. **Engineered for citation, not keywords** — names ChatGPT, Perplexity, Gemini, Google AI Overviews, *and traditional search* in the same line (the convergence beat).
  3. **Fresh signal feeds the next cycle** — closes with *"Your company must go where the conversation is today."*
  4. **We built this for ourselves.** — David-vs-Goliath origin story. Closes with *"This is that system."*
- **Visual** (right column) — logarithmic spiral + CSS 3D cube. *Detailed below*.

### 7. CTA
- **Eyebrow:** "Start with a baseline"
- **Title:** "See how visible you are *today.*"
- **Form:** email-only, button reads *"Get my baseline"* (matches "baseline" through-line)
- **Note:** *"No commitment. Your AI search baseline delivered within 5 business days — the first step in your first cycle."*
- **Thanks message:** *"Thanks — your first cycle starts here. We'll be in touch within one business day."*
- ⚠️ **Form has no backend.** Submit just hides the form and shows the thanks message. Wire up before going live.

### 8. Footer
- *"© 2026 Ramp/Jet. A self-improving growth engine for B2B."*
- Privacy / Terms / hello@rampjet.com links.

---

## Hero animation (the flywheel)

**This is the centerpiece visual.** It's a single closed CW loop with four nodes, narrating the system's continuous cycle:

```
                    Calibrate (12 o'clock)
                         ●
                       ╱   ╲
                      ╱     ╲
                     ╱       ╲ ← long CW arc through right side
        Ramp ●─────╱           ╲
       (9 o'clock)              ● Tune (3 o'clock)
                  ╲             ╱
                   ╲           ╱
                    ╲         ╱
                     ╲       ╱
                      ●─────╯
                      Jet (6 o'clock)
```

### Geometry
- **viewBox:** `0 0 480 480`
- **Loop circle:** centered (260, 240), radius 160 — drawn as a single `<circle>` with `stroke-dasharray="4 6"` (faint orange dotted line)
- **Ramp:** (100, 240) — 9 o'clock
- **Calibrate:** (260, 80) — 12 o'clock
- **Tune:** (420, 240) — 3 o'clock
- **Jet:** (260, 400) — 6 o'clock

### The cycle (every 7.2 seconds)
1. Four **satellites** fade in around Ramp; **feeler lines** extend out, then retract — pulling each satellite into Ramp's core
2. Small (r=3) **packets** emerge from Ramp every 0.9s, travel CW up the loop's left arc to **Calibrate** → Cal flashes orange + ripples on impact
3. Larger (r=5) **packets** emerge from Cal, travel CW around the loop's right side, **passing through Tune** at the midpoint — Tune's needle ticks to a new (irregular) angle each pass
4. Packets continue down to **Jet** — slot 1 of Jet's accretion ring lights up
5. The **rotating ring** of 8 slots cycles, presenting a fresh slot at the landing point every 0.9s. Eight packets fill the ring over 7.2s
6. When the ring is full, a single larger (r=6) **return packet** flies CW up the lower-left arc back to Ramp's core
7. Repeat at higher altitude (conceptually — visually identical loop)

### Specific elements

**Ramp's input system:**
- 4 satellites at static positions left of Ramp; feeler lines from Ramp center to each satellite tip
- `stroke-dasharray` animation grows the feeler outward, then retracts
- Satellites translate from their static position to Ramp center (translate values hardcoded per satellite)
- Ramp core has a subtle scale pulse on a 0.9s cycle

**Calibrate impact:**
- Cal flashes — keyframe `calibrateFlash`: at 0% scale 1.5x + fill orange, decays to scale 1 + fill black by 30%
- Cal ripple — circle with `stroke="orange"` `fill="none"` that scales 1 → 3 + fades opacity, on a 0.9s cycle delayed to first impact

**Tune dial (the irregular ticker):**
- A small cream-colored line (length 10) inside Tune's dark dot
- Uses `animation-timing-function: steps(1, jump-end)` so it **snaps** between angles (no smooth interpolation)
- Eight angles per 7.2s cycle: 0° → 73° → 215° → 142° → 308° → 31° → 187° → 264° → reset
- Hand-picked non-uniform angles so it reads as "tuning a radio" rather than orderly rotation
- `animation-delay: 2.81s` so the first tick coincides with the first packet pass-through at 3.71s

**Jet's accretion ring:**
- 8 slots arranged at radius 33 around Jet center, 45° apart
- Slot 1 is at angle 354° (almost 3 o'clock relative to Jet) — this position is **on the loop circle**, so the Cal→Jet packet can land precisely on it without an extra L-segment
- Other slots are positioned so CW rotation of the ring brings them to slot 1's "P" position at 0.9s intervals
- Ring rotates 360° per 7.2s = 50°/sec — exactly one slot-spacing per packet arrival
- Slot keyframes (`jetSlot1` through `jetSlot8`) light each slot at its arrival moment
- `animation-delay: 4.374s` for both ring rotation and slots, so the first slot lights at first arrival

**Cal→Jet packets (the trickiest piece):**
- 8 packet elements (`.packet-acc-1` through `-8`), all sharing one `offset-path` from Cal to slot 1
- Path: `M 260 80 A 160 160 0 1 1 292.8 396.6` — single 168.2° CW arc on the loop
- Each packet has its own `animation-delay`, staggered 0.9s apart starting at 2.874s
- Travel time per packet: 1.5s (20.83% of 7.2s cycle)
- All packets land at the same fixed point P, but the rotating ring presents a different "empty slot" each time

**Return packet (closes the loop):**
- Single circle (`.packet-return`), r=6
- `offset-path: path('M 260 400 A 160 160 0 0 1 100 240')` — 90° CW arc Jet → Ramp
- `animation-delay: 10.674s` — fires when Jet ring fills (slot 8 lights at 10.674s)
- Travel: 0.9s, arrives at Ramp at 11.574s — exactly when the slot cycle resets

### Timing chain (one full cycle, real-time)

| Time | Event |
|---|---|
| 0 → 4.4s | Satellites assembling at Ramp; first packet stream starts |
| 3.564s | Cal flashes (first Ramp→Cal packet impact); first Cal→Jet packet emerges |
| 3.71s | First Cal→Jet packet passes Tune; Tune's needle does its first tick |
| 4.374s | Slot 1 lights at Jet (first Cal→Jet packet arrives) |
| 5.274 → 10.674s | Slots 2–8 light at 0.9s intervals; Tune ticks each time |
| 10.674s | Ring is full; return packet emerges from Jet |
| 11.574s | Return packet arrives at Ramp; ring resets; **next cycle begins** |

### Implementation notes
- **CSS-first animation strategy** — no JavaScript timing logic. Just `@keyframes`, `offset-path`, `animation-delay`, and the occasional `transform-origin`.
- **Z-order matters.** Ramp→Cal packets are drawn before ramp-core (so they emerge from "inside" Ramp). Cal→Jet packets are drawn after Jet's slot ring (so they're visible on top until they fade into the lit slot).
- **Reduced-motion support:** all animations are `animation: none !important` under `@media (prefers-reduced-motion: reduce)`. Static fallbacks show all 8 slots lit, satellites visible, Tune needle at 0°.

---

## Approach section visual (the spiral + cube)

A logarithmic growth spiral with a 3D cube at its terminus. Conveys "each cycle compounds on the last."

### Spiral
- **viewBox:** `0 0 380 360`
- 4.25-turn logarithmic spiral, generated by Python script (radius `r₀ = 5` → `r_max = 130`, `b ≈ 0.118`)
- Center: (190, 120). Ends at (190, 250) — the spiral curves naturally to its terminus, no straight-down tail
- Drawn as 96 `L`-segment approximation in a single `<path>` with the same dotted-line aesthetic as the hero's loop
- **Three signal dots** travel the spiral over a 12s cycle, staggered 4s apart — at any moment ~3 dots are in flight at different radii, visualizing accumulation

### The cube (HTML embedded via foreignObject)
- `<foreignObject x="160" y="220" width="60" height="60">` so the cube center is at (190, 250) — the spiral's natural end
- Standard 6-face CSS 3D cube (`transform-style: preserve-3d`, `perspective: 220px`)
- **Tumble animation:** `rotateX(0 → 360deg)` + `rotateY(0 → 720deg)` over 12s — never lands the same way twice
- **Per-face morphing pulse:** each of the 6 faces has its own 6s opacity-and-color animation, **staggered 1 second apart**. As a face's pulse peaks, its background goes 18% → 42% opacity and its border brightens from accent-orange to peach (`#ff8a6b`). Because faces pulse on different beats, the cube's silhouette appears to *morph* — different faces dominate at different moments

### Why this approach
- The previous version was a generic 4-spoke flywheel diagram (CONTENT / AI SEARCH / SIGNAL / OUTREACH around "Your pipeline"). Replaced with the spiral because the spiral *is* compounding — radius growth = visibility growth.
- The cube is currently a *cube* (not a true polyhedron-to-polyhedron morph) — the staggered face pulse is the simplest way to capture the "morphing" feel from the freefrontend.com reference. **Open item:** could be upgraded to crossfading polyhedra (cube ↔ octahedron) if desired.

---

## Tier card icons

Replaced the original italic R / C / J letters with line-art SVG icons:
- **Ramp** — wedge silhouette (triangular ramp) with a filled corner accent. Slopes up to the right.
- **Calibrate/Tune** — semicircular gauge with needle, tick marks, and pivot dot.
- **Jet** — rocket with body, circular window, side fins, and small exhaust marks at the bottom.

All three use `stroke="currentColor"` so they pick up the accent orange via `.tier-icon { color: var(--accent); }`. They sit in the existing soft-orange rounded square (`56×56` with `border-radius: 16px`).

---

## Stats with sources (for reference)

| Stat | Source |
|---|---|
| 96% of pages get zero Google traffic | [Ahrefs 2023 search-traffic study](https://ahrefs.com/blog/search-traffic-study/) (analyzed 14B pages) |
| 527% YoY AI-referred web sessions | [Previsible / Search Engine Land 2025](https://searchengineland.com/ai-traffic-up-seo-rewritten-459954) (19 GA4 properties, Jan–May 2025 vs. same window 2024) |
| 5× conversion AI vs. organic | [Exposure Ninja 2026](https://www.bubblegumsearch.com/blog/ai-traffic-converts-better-than-organic/) (B2B-specific; other studies range 1.16× → 5.1×) |
| 89% of B2B buyers use AI search | [Forrester 2024 Buyers' Journey Survey](https://www.warmly.ai/p/blog/b2b-buyers-chatgpt-geo-guide); corroborated by [Profound](https://martech.org/how-chatgpt-search-reshapes-the-b2b-buyers-journey/) |
| Only 11% of domains cited by both ChatGPT & Perplexity | [Averi 680M-citation analysis](https://news.ycombinator.com/item?id=47223235) (2026) |

---

## Color palette / typography

CSS custom properties (top of `<style>`):

```css
--cream:       #f4efe6   /* page background */
--cream-deep:  #ebe4d6   /* eyebrow chip background, marquee row */
--ink:         #1a1a1a   /* primary text + dark sections */
--ink-soft:    #2c2926   /* secondary text */
--muted:       #6b655c   /* tertiary text + small labels */
--line:        #d9d2c4   /* borders */
--accent:      #e94b35   /* primary orange */
--accent-deep: #c93a25   /* primary hover */
--accent-soft: #fae3dd   /* tier-icon background */
```

Fonts (Google Fonts, all loaded via single `<link>` in head):
- **Fraunces** — display headlines (variable, weights 300–900, italic axis enabled). Used for H1, section titles, tier names, pull quote, "Your pipeline" label.
- **Instrument Sans** — body text (variable, weights 400–700, italic axis). Used for nav, hero subhead, tier descriptions, paragraphs.
- **JetBrains Mono** — small labels and eyebrows (weights 400, 500, 700). Used for ALL CAPS micro-labels, eyebrows, marquee items, source citations.

---

## Accessibility

- **`prefers-reduced-motion: reduce`** is honored throughout. Every keyframe animation that runs infinitely is disabled in this mode. Static fallbacks are defined for: feelers (drawn full), satellites (visible), Jet slots (all visible), Tune needle (no rotation), spiral signals (hidden), the cube (frozen at a tasteful 20°/45° angle).
- The rotating headline word **does not start its `setInterval` if `prefers-reduced-motion: reduce`** — checked via `window.matchMedia` in the inline script.
- All decorative SVGs in tier cards have `aria-hidden="true"` on the wrapper.
- The hero rotator uses an invisible `<span class="rotator-sizer" aria-hidden="true">DuckDuckGo</span>` to reserve width.
- The headline is a single `<h1>`. Each major section has a single `<h2>`. Sub-headings under tier cards use `<h3>` and Approach points use `<h4>`.
- Color contrast: dark text on cream is ≥ 4.5:1 across all body text. Muted text on cream is right at WCAG AA threshold for normal text and passes for large/bold.

---

## Open items (next chat / iteration list)

1. **Form backend.** The CTA email form just toggles a thanks message via inline `onsubmit`. Wire to a real endpoint (Formspree / your backend / serverless) before launch.
2. **In-page footnote markers** for stats. Currently stats have a single "Sources:" line at the bottom of the Problem section. Could upgrade to numbered `[1] [2] [3]` with anchored footnotes at section bottom for tighter credibility.
3. **Mobile audit.** Built and reviewed primarily at desktop widths. Walk through narrow-viewport behavior — especially the hero's circular flywheel SVG (currently hidden under 1024px), the marquee, and the tier cards.
4. **True polyhedron morph for Approach visual.** Current cube uses face-pulse to suggest morphing. A real cube ↔ octahedron crossfade would more faithfully replicate the freefrontend.com demo. Octahedron requires 8 triangle faces with non-orthogonal CSS 3D transforms.
5. **Optional aura rotation on Jet.** We removed `.aura-spin` (decorative dashed tick ring) when restructuring. Could be re-added as ambient motion under the slot ring.
6. **Real client logos / case studies** if/when available — would replace or supplement the proof-band marquee.

---

## File quick-reference

Key class names you'll need to know:

| Class | Purpose |
|---|---|
| `.ramp-core`, `.ramp-aura` | Ramp dot + pulsing rings |
| `.satellite`, `.satellite-1..4` | Inputs assembling at Ramp |
| `.feeler`, `.feeler-1..4` | Lines that grab the satellites |
| `.packet`, `.packet-1..4` | Ramp → Cal stream |
| `.calibrate-core`, `.calibrate-ripple` | Cal node + flash ripple |
| `.tune-core`, `.tune-needle` | 3 o'clock dot + irregular dial |
| `.packet-acc`, `.packet-acc-1..8` | Cal → Jet stream |
| `.jet-ring`, `.jet-slot-1..8` | Jet's rotating slot ring |
| `.packet-return` | Jet → Ramp closure |
| `.growth-spiral` | Approach spiral path |
| `.growth-signal`, `.growth-signal-1..3` | Spiral signal dots |
| `.poly-stage`, `.poly-cube`, `.poly-face` | The Approach 3D cube |

---

## Recent decisions / context

This is the snapshot of major decisions made this session (chronological, latest at the bottom):

- **Adopted the "continuous loop" spec verbatim** across Hero subhead, Problem section, How It Works, Approach, Pull Quote, CTA, Footer. Voice/tone guidelines applied throughout.
- **Resolved the four spec tensions:** marquee + Problem rolled back to spec-pure copy, hero subhead adopted system narrative (drops "geographies"), Approach visual was rebuilt as the spiral instead of the original 4-spoke flywheel, system positioning chosen over leads-as-headline.
- **Hero became a true flywheel** (closed CW loop, not open trajectory + return arc). Jet moved to 6 o'clock for clean alignment. Tune added at 3 o'clock with the irregular-tick needle. Slot ring repositioned so slot 1 sits on the loop circle (eliminates the "snap" at packet arrival).
- **Approach visual was rebuilt** twice: first as a logarithmic spiral with traveling dots (replacing the 4-node flywheel), then upgraded with a 3D CSS cube at the spiral's end (replacing first the morphing polygons, then the shimmering sphere).
- **Sourcing pass:** all four AI-search stats verified against real sources; added a 96% legacy-SEO stat (Ahrefs) and a Sources line.
- **Headline tightened** to *"Search is mission critical. Now it's changing. Most companies have no idea."* Body lands on *"You need a system. You need Ramp/Jet."*
- **Tier name tweaks:** PHASE 01 / Configure, PHASE 02 / Optimize (with name "Calibrate/Tune"), PHASE 03 / Accelerate. Tagline for tier 2: "Refine the system."
- **Approach copy revisions:** Point 01 reframed as "A flywheel, not a one-time project" with the conversational "Could you use Ramp/Jet for one cycle and call it quits?" opener. Point 04 re-anchored as "We built this for ourselves." (David-vs-Goliath story).

---

*End of build doc. If you're picking this up in a new chat, this should give you everything you need to keep going. The page is one HTML file, the positioning is locked in, the animations are well-commented in the source, and the open items are flagged above.*
