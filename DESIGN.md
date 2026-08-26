# Rampjet Site — Design Document

> **Status note (added when this was checked into the repo, Aug 2026).** This is the delivered spec, kept verbatim. The homepage has since been built from it — see [BUILD.md](BUILD.md) for what actually shipped, including three deliberate departures from this document. Sections covering the Rework/Reach/Run product pages and `/advisors` are still unbuilt. This file is excluded from the published site via `_config.yml`; keep it that way.

**Purpose.** Evolve the live Rework site (reworkbyrampjet.com) into a Rampjet house site with three product landing pages: Rework, Reach, Run. This document is the source of truth for structure, copy, design tokens, and open decisions. A working HTML mock of the house page ships alongside it (`rampjet-homepage.html`); treat the mock as a reference for layout and tone, and this document as the spec.

**Scope of this pass.** Add the house page, add Reach and Run landing pages on the Rework template, make targeted edits to the existing Rework page, and move the advisor content to a single house-level page. Do not restyle Rework. Do not introduce a framework; the live site is static HTML/CSS/JS and should stay that way.

---

## 1. Positioning (read this before writing any copy)

**Who it's for.** Owner-operated industrial companies, roughly $5–50M: machine shops, fabricators, distributors, contract manufacturers, specialty suppliers. The defining condition: the owner is still the system. Sales, quoting, and customer knowledge route through one or two people.

**The one-sentence position.** Rampjet takes industrial companies where the owner is still the system and builds the systems the company runs on when the owner isn't in the room.

**The territory claim.** Everything from the first search to the ERP. Rampjet builds and maintains the half of the business that runs on email, spreadsheets, and memory: website → inquiry → follow-up → quote → job tracking and customer records. It stops where the ERP starts. "ERP" must always be glossed so that QuickBooks-and-a-whiteboard counts ("or your accounting system, or whatever you run the shop on").

**House headline.** *Get the business out of your head.* This is what the owner already says about themselves. It implies both efficiency and transferability without naming either.

**Three products, à la carte or together.**

| Product | Slot | Customer's sentence | Price shape |
|---|---|---|---|
| Rework | The website | "Our site doesn't look like the work we do." | $2,000 one-time (+ Maintain $200/mo) |
| Reach | The demand engine | "We get leads and nobody follows up." | Monthly |
| Run | Operations | "Quotes wait on me." | Per project, fixed price, scoped first |
| The Full Build | All three, one plan | — | One build price + Reach monthly; less than three separate engagements |

**Exit / sale-prep is not public copy.** It lives on one advisor page (`/advisors`) reached only from a footer link. Product pages and the house page never say "exit," "sale," "buyer," or "valuation." Public-facing language is "runs without you" and "transferable," never "for sale."

**Words to avoid anywhere on the site.** Infrastructure, modernize, digital transformation, AI (as a headline or selling point), automation platform, solution, seamless, leverage, empower. The buyer fears rip-and-replace; every section should read as "we connect what you have."

**Voice.** Plain, short, shop-floor. Sentences an owner would say out loud. Concrete over abstract. The existing Rework page is the calibration; match it.

---

## 2. Information architecture

### 2.1 URLs

```
rampjet.com/                → House page (new)
rampjet.com/rework          → Rework landing page (existing content, moved + edited)
rampjet.com/reach           → Reach landing page (new)
rampjet.com/run             → Run landing page (new)
rampjet.com/advisors        → Advisor page (consolidated from Rework's advisor section)
reworkbyrampjet.com/*       → 301 → rampjet.com/rework (and /rework-advisor-one-pager.html → /advisors)
```

Rationale: three product domains would look like three companies and split search authority. One domain, three paths. "Rework by Rampjet" stays as the product wordmark; only the URL consolidates.

If rampjet.com is not available for this at the moment, the interim structure is reworkbyrampjet.com as-is plus `/reach`, `/run`, `/advisors`, and a house page at `/` that replaces the current Rework homepage (Rework moves to `/rework`). Same architecture, different domain.

### 2.2 Global navigation

**Header (all pages):** wordmark left; links `Where we work · Rework · Reach · Run · The Full Build`; orange button `Book a call` right. On product pages, the product's own link is highlighted. Mobile: wordmark + button only, links in a collapsed menu.

**Footer (all pages):** wordmark; links `Rework · Reach · Run · Full Build · For advisors`; tagline `© 2026 Rampjet · Systems for industrial companies`. "For advisors" appears **only** here.

### 2.3 Wordmark

House: `RAMP/JET` in Archivo 900, uppercase, slash in orange. Product pages: `REWORK — by Ramp/Jet` (existing lockup), and matching `REACH — by Ramp/Jet`, `RUN — by Ramp/Jet`. The existing Rework SVG lockup is the canonical asset; derive the other two from it, do not redraw. Open item: the site currently mixes "Ramp/Jet" and "Rampjet"; standardize on `Ramp/Jet` in wordmarks and `Rampjet` in running text.

### 2.4 Cross-linking

Every product page carries an "Also from Rampjet" strip above the footer: two small cards for the other two products (name, customer's sentence, price shape, link) plus a one-line link to The Full Build. The house page is the only page that carries the order form and the territory map in full.

---

## 3. Design system

Inherited from the live Rework site. Do not change values; extend only where a new component needs one.

### 3.1 Tokens

```css
:root {
  --steel:    #0E1013;   /* primary dark bg */
  --steel-2:  #1B1F23;
  --steel-3:  #262B31;
  --paper:    #F9F6F1;   /* primary light bg */
  --bone:     #ECEAE4;   /* secondary light bg, cards */
  --ink:      #14171A;   /* text on light */
  --mute:     #6B7076;   /* spec labels on light */
  --mute-lt:  #A9AEB3;   /* spec labels on dark */
  --orange:   #C2603F;   /* accent, buttons, claim bars */
  --orange-dk:#A54E31;   /* accent on light bg text */
  --orange-lt:#D46E4B;   /* button hover */
  --line:     rgba(20,23,26,.14);
  --line-dk:  rgba(249,246,241,.14);
}
```

### 3.2 Type

- **Display:** Archivo 800/900, uppercase, letter-spacing −0.01em, line-height 1.02. H1 `clamp(44px, 6vw, 76px)`. H2 `clamp(32px, 4.4vw, 56px)`.
- **Body:** IBM Plex Sans 400/500/600. Body 17–19px on light, `#3A3F44` for paragraph text (not pure ink).
- **Spec / label:** IBM Plex Mono 400–600, 11–13px, uppercase, letter-spacing 0.08–0.12em, `--mute`. Orange variant for section eyebrows.
- **Stamp:** Space Mono for work-order numbers, "Op 10" labels, and the rotated "check what you need" tag.

Load via Google Fonts as on the mock. No other typefaces.

### 3.3 Components (existing vocabulary)

- **Work-order card.** Paper card, 2px ink border, orange hard shadow offset 10px/10px, bone header strip with mono title + document number (`RJ-2026-0001` style). Rows are mono key/value with dashed dividers. This is the hero object on every page.
- **Spec sheet.** Bone card, 1px line border, ink header bar with reversed mono text, mono key/value rows. "Does not include" row values in `--orange-dk`. Used in product cards on the house page and in the price section on product pages.
- **Op routing.** Grid of stages separated by 2px ink rules, `Op 10 / Op 20 / …` stamp labels in orange, arrow glyph overlapping the divider. Used for "how it works" on product pages and for The Full Build on the house page.
- **Buttons.** Solid orange, mono 600 14px uppercase, 16px/22px padding, no radius. Ghost variant: transparent with 2px inset ink border. Hover: `--orange-lt` / inverted.
- **Section eyebrow.** Orange mono spec line above every H2.
- **Quote card.** Paper card with a 6px orange left rule, Archivo 700 22px quote, mono attribution.

No border-radius anywhere. No drop shadows other than the hard orange offset. No gradients. No icons except the arrow glyph in buttons and the ✕ in the don't-do list.

### 3.4 Motion and accessibility

- Respect `prefers-reduced-motion`; no animation is required anywhere.
- `:focus-visible` outline: 3px orange, 3px offset, on every interactive element.
- Checkboxes in the order form must be real `<input type="checkbox">` inside `<label>`; the visual is CSS on top.
- The territory map must remain readable as a linear list on mobile (see §4.2).

---

## 4. House page — `rampjet.com/`

Section order and copy. Copy is final unless marked **[PLACEHOLDER]** or **[DECISION]**.

### 4.1 Hero (dark)

- Eyebrow: `Rampjet · For owner-operated industrial companies`
- H1: `Get the business out of your head.` ("out of your head." in orange)
- Sub: `We build the website, then the demand engine behind it, then the quoting, tracking, and follow-up systems your team is still running out of spreadsheets and memory. Everything from the first search to the ERP. We connect what you already have, and we stop where your ERP starts.`
- CTA: `Book a 45-minute call →` + spec text `Buy one. Or all three.`
- Right column: **the order form** (§4.6).

### 4.2 Where we work — territory map (bone)

- Eyebrow: `Where we work`
- H2: `Everything up to the ERP.`
- Intro: `The ERP (or QuickBooks, or the whiteboard) is where a job goes once it's won. Everything before that line runs on email, spreadsheets, and memory. That's our side. We never cross it.`
- **The map.** A bordered grid: top row is claim bars (orange 8px rule + product name + slot label), bottom row is six stages, and a full-height dark column on the right for the ERP.
  - Stages: `1 A buyer searches · 2 They find your site · 3 An inquiry comes in · 4 Someone follows up · 5 A quote goes out · 6 The job is tracked and won`
  - Claims: Stage 1 = "Not ours" (no bar). Rework = stage 2. Reach = stages 3–4. Run = stages 5–6.
  - ERP column (steel bg, orange left rule): stamp `The line`, `Your ERP`, `Or your accounting system, or whatever you run the shop on today. Yours. Untouched. We hand off clean and stop.`
  - Legend: `Orange bar = what Rampjet builds and maintains. Stage 1 is the buyer's; the last column is yours.`
- **Mobile:** collapse to a single column in this order: Stage 1, Rework claim, Stage 2, Reach claim, Stage 3, Stage 4, Run claim, Stage 5, Stage 6, ERP. Use CSS `order`; the mock implements this.
- **[DECISION]** Bar placement is a guess at scope boundaries. If Reach touches quoting, or Run reaches back into follow-up, move the bars. The stage wording should use customers' own phrasing if it differs.

### 4.3 Who this is for (paper)

- Eyebrow: `Who this is for`
- H2: `Where the owner is still the system.`
- Four list items, orange dash bullet, bold lead:
  - **Industrial, owner-operated, roughly $5–50M.** Machine shops, fabricators, distributors, contract manufacturers, specialty suppliers.
  - **Sales still route through one or two people.** The best customers are relationships, and the relationships live with the owner.
  - **Quotes wait on whoever knows the job.** The pricing logic is in someone's head, and the spreadsheet is a memory aid, not a system.
  - **The website was last touched when the last guy left.** It works, mostly. It doesn't look like the work.

### 4.4 Three products (paper)

- Eyebrow: `Three products` · H2: `Each one stands on its own.`
- Side note: `You don't need the website to buy the follow-up system. You don't need either to fix quoting. Start where it hurts.`
- Three full-width rows, 2px ink rules between. Layout: left = product tag (orange swatch, name in Archivo 900 34px, slot label mono); middle = customer's sentence as an Archivo 800 quote with orange quote marks, then two short paragraphs; right = spec sheet with a CTA link.

**Rework**
- Sentence: `Our site doesn't look like the work we do.`
- P1: `A professional site, rebuilt in two days from the first call. Full brand system, hosting included, two revision rounds. We manage it so you don't have to, and inspect it every quarter at no charge.`
- P2: `Flat price. No scope creep. If Rework isn't the right fix, we'll tell you on the call.`
- Spec: Price **$2,000** one-time · Lead time 2 days from first call · Includes Brand system · hosting · quarterly inspection · Option + Maintain, $200/mo · **Does not include** Lead follow-up after the form · CTA `Start with Rework →` → `/rework`

**Reach**
- Sentence: `We get leads and nobody follows up.`
- P1: `Every inquiry — web form, email, phone — gets captured, routed to the right person, and followed up on a schedule that doesn't depend on who's busy. You see what came in, who touched it, and what closed. The system watches what works and adjusts.`
- P2: `Sits on a Rework site or on the site you already have, if we can wire into it. Revenue stops depending on who the owner knows.`
- Spec: Price **$750** per month **[PLACEHOLDER]** · Live in 2 weeks **[PLACEHOLDER]** · Includes Capture · routing · follow-up · weekly report · Requires A site we can instrument · **Does not include** Quoting or internal ops · CTA `Start with Reach →` → `/reach`

**Run**
- Sentence: `Quotes wait on me.`
- P1: `One process at a time — quoting, job tracking, customer records, scheduling — pulled out of one person's head and into a system anyone on your team can run. We start with the thing that's costing you the most and scope it before we touch anything.`
- P2: `We connect to what's already there: QuickBooks, the spreadsheet, the shared drive, the phone. Nothing your people have to relearn their job to use.`
- Spec: Price **from $3,500** per project **[PLACEHOLDER]** · Scoped Fixed price before we start · First projects Quoting · job tracking · customer records · Works with What you already use · **Does not include** Marketing or the website · CTA `Start with Run →` → `/run`

### 4.5 What we don't do (dark)

- Eyebrow: `Worth saying out loud` · H2: `What we don't do.`
- Body: `Most of what you've been pitched before is on this list. We work up to the ERP, not on it. The absence of the rest is the point.`
- Two-column list, orange ✕, Archivo 700 uppercase: `No ERP replacement · No six-month rollouts · No rip-and-replace · No "digital transformation" · No AI as a headline · Nothing your team has to relearn`

### 4.6 The order form (hero object)

Work-order card. Header `ORDER FORM` / `RJ-2026-0001`. Hint row `Line items — check one or all three`. Three checkbox line items:

| Name | Description | Price (right) |
|---|---|---|
| Rework | Your website, rebuilt in two days. | $2,000 / one-time |
| Reach | Every inquiry captured, routed, and followed up. | $750 / per month **[PLACEHOLDER]** |
| Run | Quoting, tracking, and records out of one person's head. | from $3,500 / per project **[PLACEHOLDER]** |

Total row (label `Your order`) with a button. Behavior:
- Nothing checked → `Nothing checked yet. Start with the one that hurts.` Button `Book a call`.
- One checked → `<Product>, <shape>. Scoped and priced on the call.` Button `Start with <Product>`.
- Two checked → `<A>, <shape> + <B>, <shape>. Scoped and priced on the call.` Button `Book a call`.
- All three → `That's The Full Build. One build price, one plan, bundled on the call.` Button `Talk Full Build`.
- Optional enhancement: pass the selection to the booking link as a query string (`?items=rework,run`) so the call form or Calendly note is pre-filled. Vanilla JS, no dependencies.

### 4.7 The Full Build (paper)

- Eyebrow: `All three, one plan` · H2: `The Full Build.`
- Sub: `For the owner who's already tired and wants one team to own the whole thing. Built in order, on one work order, for less than three separate engagements.`
- Op routing, three cells:
  - **Op 10 Rework · Weeks 1–2** `The site goes up first. It's the front door everything else attaches to, and it's the fastest visible win.`
  - **Op 20 Reach · Weeks 2–4** `Capture and follow-up go live on the new site. From here, no inquiry waits on the owner.`
  - **Op 30 Run · Month 2 onward** `First internal process scoped and built — usually quoting. Then the next one. Each priced before it starts.`
- Foot strip (bone): `One build price for Rework + the first Run project, plus the Reach monthly. Bundled price on the call.` + button `Talk about the Full Build`.
- **[DECISION]** Whether to publish a bundle number or keep it "on the call."

### 4.8 Proof (bone)

- Eyebrow: `What it looks like when it works` · H2: `Before and after, in the owner's words.`
- Three quote cards with product · industry attribution.
- **[PLACEHOLDER]** All three quotes in the mock are illustrative and must be replaced with real statements (Fluid Tech, Filmax, others) before launch. The Rework page's before/after imagery pattern is the model; if real screenshots exist for Reach/Run outputs (a follow-up log, a quote that used to take a day), use those instead of quotes.

### 4.9 Book the call (paper)

- Eyebrow: `Book the call` · H2: `Forty-five minutes. Then it's off your desk.`
- Body: `Tell us which of the three hurts most. If none of them is the right fix, we'll say so on the call and you've lost nothing but the coffee.`
- Button `Pick a time` → Calendly (existing link is 30-min; **[DECISION]** create a 45-min event or change copy to thirty). Optional "Or send a note" form as on Rework.

---

## 5. Product landing page template

All three product pages use the same skeleton. Rework's live page is the reference implementation; Reach and Run fill the same slots. Keep section IDs consistent (`#how`, `#proof`, `#ongoing`, `#price`, `#faq`, `#book`) so nav anchors match across pages.

| Slot | Rework (live) | Reach | Run |
|---|---|---|---|
| Eyebrow | Websites for industrial companies | Demand engine for industrial companies | Operations for industrial companies |
| H1 | Your website, fixed in *two days.* | Every inquiry, *followed up.* | Quoting that doesn't *wait on you.* |
| Sub | Fixed price. Fixed timeline. No four-month project. | Captured, routed, and chased until it closes or it's dead. No inquiry waits on the owner. | One process at a time, out of one person's head and into a system your team runs. Scoped and priced before we start. |
| Hero work-order rows | Turnaround / Revisions / Price / Hosting / Inspection | Live in / Channels / Response time / Price per month / Report | First project / Scoped in / Price / Works with / Next project |
| Why this exists | "The site was fine in 2011." | "The lead came in Tuesday. Somebody saw it Friday." | "Everyone knows the price. One person can produce it." |
| How it works | Op 10–40, two days | Op 10–40, two weeks: Wire / Route / Chase / Report | Op 10–40 per project: Scope / Build / Hand off / Review |
| Proof | Before/after site screenshots | Follow-up log before/after; days-to-first-touch | A quote before/after; hours-to-quote |
| Ongoing mechanism | Quarterly inspection (free, forever) | Weekly report (built in) | Quarterly ops review that names the next process |
| Price | Rework $2,000 / Rework + Maintain +$200/mo | Reach $[X]/mo, single tier | Run per project from $[X] / Run + Own, monthly retainer for "the next thing" |
| Straight answers | existing FAQ | see §5.2 | see §5.3 |
| Book the call | 30 min | 30 min | 30 min |
| Also from Rampjet | new strip | new strip | new strip |

### 5.1 Rework page edits (targeted, no restyle)

1. Move content to `/rework`; redirect the old root.
2. Header wordmark unchanged; nav becomes the global nav (§2.2). Remove `For advisors` from header.
3. Remove the **Rework for Advisors** and **Transfer Packet** sections and the advisor FAQ entries ("I'm an advisor…", "Can the buyer keep using you after close?"). This content moves to `/advisors` (§6). Keep the one-pager file; link it from `/advisors` only.
4. Add the "Also from Rampjet" strip above the footer.
5. Footer tagline → `Systems for industrial companies`; add `For advisors` footer link.
6. Leave everything else as-is: hero, work order, "The site was fine in 2011," Ops, before/after, inspection, price, FAQ, book.

### 5.2 Reach page — content notes

- **The ongoing mechanism is the product.** The weekly report is what the owner sees; it should be shown as a sample the way Rework shows a sample inspection: a short list with Pass / Fix / Note / Opp. labels (e.g., `11 inquiries this week · 11 first-touched within 1 hour · 2 quoted · 1 stalled — owner has it`).
- **Requires** an instrumentable site. Say plainly: works on a Rework site or an existing site we can wire into; if we can't, we'll tell you on the call and Rework is the fix.
- **Does not include** quoting or anything past the inquiry. Point to Run.
- FAQ seeds: *Do you replace my CRM?* (No; if you have one we write into it) · *Who does the follow-up, you or us?* · *What counts as an inquiry?* (form, email, phone, walk-in logged) · *What happens to a lead nobody wants?* · *Can I turn it off?* (any month; the log is yours).
- **[PLACEHOLDER]** Price, live-in time, response-time commitment.

### 5.3 Run page — content notes

- **One process per project.** Name the usual first three (quoting, job tracking, customer records) and say the first one is whichever costs the most today.
- **Scope before build.** The Op 10 cell is the scoping call that ends in a fixed price; nothing is built before that.
- **Works with what's there.** Name real things: QuickBooks, the spreadsheet, the shared drive, the phone. Never name an ERP as something Run touches.
- **The ongoing mechanism:** quarterly ops review that identifies the next process and prices it. This is what turns Run from a project into a relationship and matches the customer behavior that prompted the product.
- **Second tier:** "Run + Own" (name **[DECISION]**): a monthly retainer where Rampjet owns the next-thing queue. This is the shape customers are already asking for when they say "can you also do X."
- FAQ seeds: *Is this an ERP?* (No; we stop where yours starts) · *Will my people have to learn new software?* · *What if the process is in one person's head and they don't want to give it up?* · *Who owns what you build?* (You do; source, data, logins) · *What's the smallest thing you'd do?*
- **[PLACEHOLDER]** Starting price, retainer price, review cadence.

---

## 6. Advisor page — `rampjet.com/advisors`

The only place exit/sale language appears. Not in header nav; footer link only. Not indexed prominently (no need to noindex, but do not link it from product pages except the footer).

- Move the existing Rework advisor section, Transfer Packet, confidentiality/fee notes, and the two advisor FAQ items here, largely as written.
- Extend the frame from "the website is a small, cheap chip in the runs-without-the-owner column" to the three-product version: Rework closes the visible item in week one; Reach makes demand auditable (an inquiry log a buyer can read); Run puts the operating processes on paper. The Transfer Packet grows from digital footprint to digital footprint plus documented processes and system access for anything Run built.
- Keep the honesty line: a website is not a multiple play. Do not claim Run raises valuation either; claim it removes key-person risk from diligence.
- Timing sentence: the window is 2–5 years out; an owner closing in 12 months wants minimal spend and we'll say so.
- Link the advisor one-pager; plan a refreshed one covering all three (out of scope for this pass).

---

## 7. Open decisions and placeholders (collect before launch)

1. Reach monthly price; Run starting price; Run retainer price and name.
2. Publish a Full Build bundle number, or keep "on the call."
3. Territory map bar placement (does Reach touch quoting? does Run reach back into follow-up?) and stage wording.
4. Calendly: 45-min event vs. changing house copy to thirty minutes.
5. Real proof statements and screenshots for Reach and Run; replace all illustrative quotes.
6. Wordmark standardization (Ramp/Jet in lockups, Rampjet in text) and the Reach/Run lockups derived from the Rework SVG.
7. Domain: rampjet.com now, or interim on reworkbyrampjet.com.

---

## 8. Implementation notes for Claude Code

- Keep the site static. One CSS file for the shared system (tokens, type, components from §3), one small per-page file only if needed. No build step required.
- Start from the live Rework page's markup for the product template; do not start from the mock for product pages. Use the mock only for the house page and for the two new components (order form, territory map), which can be lifted directly.
- Section IDs and nav anchors must match across all product pages.
- Order form and any nav toggle: vanilla JS, progressive enhancement, no dependencies.
- Images: follow the existing `/img/before-*.jpg` / `after-*.jpg` naming for any Reach/Run proof images.
- Redirects: 301 map from reworkbyrampjet.com paths to the new paths; preserve the one-pager URL via redirect to `/advisors`.
- Check every page at 390px and 1280px. The territory map's mobile order (§4.2) and the order form's line-item layout are the two components most likely to break.
- Grep the finished site for the avoid-list words in §1 and for "exit," "sale," "buyer," "valuation," "transaction" outside `/advisors`.
