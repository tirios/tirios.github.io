# Tiri Pestrivas Design System

An editorial-Swiss design language for **Tiri Pestrivas** — PhD statistician, research scientist in applied AI and R&D, Bayesian modelling. White paper, hairline rules, one grotesque in many weights, monospace for every number, and a single hue held back for links and the first data series.

The brief was a "grown-up" sibling of the existing **Tiri** hardware-sampler system: *Teenage Engineering lite*. That means the engineering mindset survives — exact numbers, uppercase micro-labels, grid discipline, nothing decorative — while the retro-industrial costume does not. No cream casing, no 1px black outlines around everything, no orange LEDs, no hard offset shadows.

The organising rule, and the one that matters most:

> **The interface is achromatic. Colour belongs to the data.**

Chrome is graphite. Teal marks a link, the single primary action, and the first data series. Everything else — ochre, slate, clay, plum — exists only inside a chart.

## What this is built from

| Source | What it gave us |
| --- | --- |
| The **Tiri design system** (a separate design-system project in this workspace, read in full: `readme.md`, `tokens/*.css`, component inventory, `ui_kits/`) | The lineage: colour-as-signal, exact numeric readouts, uppercase silkscreen micro-copy, the ban on gradients and emoji, "state the fact and the consequence" error copy. Its palette, type and structural vocabulary were deliberately **not** carried over. |
| Written brief supplied in chat | Audience (academic peers, industry clients, hiring managers, curious public); direction (editorial journal, all-grotesque, light only); accent `#0F766E`; the eight surfaces to cover; the four data-viz families that matter. |

**No codebase, Figma file, font binaries, logo files, icon set, portrait or slide template were provided.** Everything visual here is derived from the brief. The UI kits are plausible reconstructions of a personal site and an internal model tool — treat their content as fixture data and their layout as canon.

---

## Content fundamentals

The voice is a competent researcher explaining something to a peer who is not in their subfield. Declarative, first person, unhedged, and completely free of salesmanship.

**Person.** First person singular, used plainly: "I build models that say how sure they are." Not "we" (there is no we), not the third-person academic passive on the personal site — though the passive is correct inside a paper or report, where the report's own voice is impersonal ("Four chains were run…" → in practice: "Four chains, 1,000 warmup and 2,000 sampling iterations each.").

**Sentence shape.** Short declaratives, often ending on the concrete thing. A three-item list is the house rhythm: "Most of my work is hierarchical, most of it is fitted in Stan, and most of the difficulty is in the priors." Avoid subordinate clauses stacked more than one deep.

**Claims carry their uncertainty.** Never "the effect is 0.31." Always "the effect is 0.31 (94% HDI 0.08–0.54). It is probably positive. It is not precisely estimated." Where a caveat exists it goes in the body, not a footnote, and not after the ask.

**Headings.** Sentence case, no terminal punctuation, usually a noun phrase: "Partial pooling", "What the table does not say", "In production". Section numbers are mono and separated with a middle dot: `2.1 · Partial pooling`.

**Micro-copy (uppercase).** The only caps in the system: section eyebrows (`SELECTED WORK`), field labels (`PRIOR SCALE σ₀`), table headers (`ΔELPD`), badges (`CONVERGED`), plot axis labels (`WEEKS OF HISTORY`), and mono technical notes (`4 CHAINS · 2,000 DRAWS`). Never on buttons, headings or prose.

**Buttons.** Sentence case, verb-first, two or three words: "Read the paper", "Refit model", "Export draws". Not "SUBMIT", not "Learn more →" as a standalone.

**Numbers.** Always mono, always at real precision. `0.938`, not `~94%`. `−4,126` with a true minus sign. Dates are ISO only: `2026-02-14`. Intervals are written `94% HDI 0.08 – 0.54` with spaced en-dash. Counts of anything sampled are given with their method: `4 chains · 2,000 post-warmup draws each`.

**Errors and empty states.** State the fact, then the next step, and stop. "No runs yet — fitted models appear here once a run completes." No apology, no exclamation mark, no "oops".

**Emoji: never.** Not in UI, not in prose, not in slides. Unicode is used only where it is typographic or mathematical: `×`, `·`, `±`, `—`, `σ`, `τ`, `μ`, `R̂`, `↗`.

**Forbidden register.** "Leveraging", "unlock", "transformative", "cutting-edge", "passionate about", "insights", "journey", any sentence that could appear on a consultancy homepage. `guidelines/brand-voice.card.html` carries the write/don't-write pairs.

---

## Visual foundations

### Colour
A nine-step cool graphite ramp (`#141618` → `#F7F8F9`), pure white paper, and one hue: teal `#0F766E`. Teal appears as links, the single primary button, the active `P(θ>0)` figure, the 2px rule over an accent callout, and data series 1. If a screen shows more than about three teal marks, something that is not an action has been coloured.

The data palette is six desaturated, near-equal-value hues — teal `#0F766E`, slate `#2F5C7E`, ochre `#B07A21`, clay `#A6553F`, plum `#6B4A78`, graphite `#5A6167` — assigned in order and never reordered for looks. Interval fills use the series colour at **12%** (outer, e.g. 94%) and **26%** (inner, e.g. 50%); those two numbers are tokens (`--plot-band-soft`, `--plot-band-strong`) and are the only alpha values in the system besides shadow and scrim.

Ink on white measures 18.1:1; secondary 6.3:1; tertiary (captions, micro-labels) 4.6:1; teal 5.5:1 both ways against white. There are **no gradients anywhere**, no tinted surfaces beyond `#F7F8F9` and `#EFF1F2`, and no dark mode — the brief asked for light only.

### Type
**Schibsted Grotesk** in four weights carries every register; **JetBrains Mono** carries every number. There is no serif. Hierarchy comes from size and weight, never from a second family.

Display 84/62/46px at −0.035em semibold; headings 34/26/20px at −0.022em; prose 17px/1.62 capped at 66ch; interface body 15px/1.45; captions 12px; micro-labels 10px semibold at +0.1em uppercase; mono micro at 11px +0.14em uppercase; plot ticks 9px mono. Tracking tightens as type grows and opens as it shrinks. Functional text never drops below 11px; 9–10px is reserved for plot furniture and technical print.

Mono is not decorative. It marks *machine-reported* content: measurements, intervals, dates, run ids, formulas, code, file paths, axis ticks. A number typed by a human into prose ("three weeks of history") stays in the sans.

### Layout
A 1180px page at a 40px inset, on a 12-column grid with 24px gutters. Three recurring shapes:

- **Index pages** — single column, content in hairline-ruled rows with a mono index or date in a fixed left gutter. No cards.
- **Articles** — 200px contents rail / prose column / 240px sidebar, both rails sticky. Prose caps at 66ch even when the column is wider.
- **Tools** — fixed 272px left rail, fluid centre, fixed 292px right rail, each scrolling independently under a 56px header.

Spacing is a 4px grid (2px exists for optical nudges only). 8–16px inside a block, 32–40px between sections, 72–96px between major page regions. Control heights are fixed at 28 / 36 / 44px with nothing in between; the site header is 64px, the app header 56px.

### Borders, radii, cards
Three rule weights and no more: hairline `#E3E6E8` (row dividers, panel edges), mid `#C4C9CC` (control outlines), ink `#141618` (section heads, table headers, the rule above a pulled-out figure). A 2px accent rule appears only on the top edge of a callout.

Radii: 0 for panels, figures and tables; 2px for tags; 4px for controls; 6px for overlays; full round only on status dots and slider thumbs. A "card" here is a `Panel` — square corners, a rule, optional grey ground, **no shadow**. There are no drop-shadowed white cards, no rounded panels, and no left-accent-border cards.

### Depth and shadow
Paper does not float. Shadow means "this overlays the page": `--shadow-popover` for tooltips and menus, `--shadow-overlay` for dialogs. A near-invisible `--shadow-card` exists for hoverable list items and is used almost nowhere. Nothing in the page flow carries a shadow, nothing has an inner glow, and no shadow is coloured.

### Motion
80ms instant (checkbox tick, tab switch) · 120ms fast (hover, focus ring, tooltip) · 180ms base (dialog rise, drawer) · 260ms slow (page fades) · 420ms plot (a band or bar redrawing). Easing is `cubic-bezier(0.2,0,0,1)` everywhere. No springs, no bounce, no overshoot, no stagger. Dialogs rise 4px and fade; they do not scale. Nothing animates on page load except, optionally, a plot drawing itself in.

### Hover, press, focus, disabled
Hover is a colour change only — primary darkens to `#0B5C56`, quiet outlines darken from mid-grey to ink, ghost buttons take a `#F7F8F9` ground, links pick up a full-strength underline. Press darkens one further step (`#0A4F49`) with **no translation and no scale** — the mechanical key-travel of the ancestor system is deliberately gone. Focus is a 2px teal ring with a 2px paper offset. Disabled is `#F7F8F9` ground, `#9BA1A6` ink, hairline border, no shadow.

### Transparency, blur, imagery
Blur is never used. There is no glass, no frosted chrome, no protection gradient — a label that needs separation gets its own bordered zone or a `#F7F8F9` ground. Transparency appears in exactly three places: shadow alphas, the flat 40% ink dialog scrim, and the two interval-fill opacities.

Imagery, when supplied, should be cool, even, unfiltered and ungrained: a plain portrait on a neutral ground, and real figures exported from papers. **No imagery was supplied**, so `Figure` with no children renders a dashed grey well with a mono caption stating the intended dimensions. Use that rather than substituting stock or generated pictures.

### Links
Teal, 1px underline in `--tp-teal-300` at 2px offset; on hover the colour deepens to `#0A4F49` and the underline goes to full strength; active is `#0A4F49`. Navigation "links" in chrome are unstyled buttons that take a 1px ink underline when current.

### Charts
Charts are typography, not decoration. Every one is built on `PlotFrame`: 1px `#C4C9CC` axes, `#EFF1F2` grid, 9px mono ticks, uppercase mono axis labels, a title in sans and a right-aligned uppercase mono note. Always show the interval, not only the point. State `n` and the method in the caption. Density plots have **no y-axis** — density height is not a readable quantity. Never a pie, a donut, a 3D anything, a gradient fill, or a truncated y-axis on a bar chart.

---

## Iconography

**No icon set was supplied.** **Flagged substitution:** the system uses [Phosphor Icons](https://phosphoricons.com) at **regular (stroke) weight**, loaded from CDN per page:

```html
<link rel="stylesheet" href="https://unpkg.com/@phosphor-icons/web@2.1.1/src/regular/style.css">
```

`Icon`, `Button` and `IconButton` take a bare Phosphor name (`icon="arrow-up-right"`). Rules: regular weight only — never fill (that is the ancestor system's signature), never mixed with a second family. 16px inline, 18px in controls, 24px standalone. Icons inherit `currentColor`, are never coloured independently of their label, and never appear without a label or an accessible name. Do not hand-draw SVG glyphs and do not use emoji.

Set in use: `arrow-right`, `arrow-left`, `arrow-up-right`, `download-simple`, `file-text`, `link-simple`, `envelope-simple`, `magnifying-glass`, `caret-down`, `check`, `x`, `play`, `arrows-clockwise`, `circle-notch`, `sidebar-simple`, `sliders-horizontal`, `dots-three`, `function`, `flask`, `chart-line-up`, `git-branch`, `sigma`, `graduation-cap`, `calendar-blank`.

Unicode carries the typographic and mathematical marks: `×`, `·`, `±`, `—`, `↗`, `σ`, `τ`, `μ`, `φ`, `β`, `R̂`, `Δ`.

## Brand assets

`assets/` is **empty of marks by design** — no logo, monogram, portrait or illustration was supplied, and none was drawn. Wherever a mark belongs, the name is set in type: Schibsted Grotesk Semibold, −0.03em, sentence case, optionally over a lowercase mono strapline (`applied ai · bayesian modelling`). See `guidelines/brand-wordmark.card.html` for the three approved grounds. **Send real files and they go in.** Full detail in `assets/README.md`.

---

## Substitutions to resolve

1. **Fonts.** No binaries supplied. Google Fonts **Schibsted Grotesk** (the grotesque; chosen for a real weight range and slightly humanist digits) and **JetBrains Mono** (unambiguous `0`/`O`/`1`/`l`, even colour at 11px), loaded by `@import` in `tokens/fonts.css`. Swap for local `@font-face` rules when licensed files arrive.
2. **Icons.** Phosphor regular weight from CDN, as above.
3. **Logo.** Absent; type-only wordmark in use.
4. **Imagery.** Absent; captioned dashed placeholder wells in use.
5. **Content.** Every publication, project, grant, number and quotation in the UI kits is fixture data. None of it is Tiri's real record.

---

## Index

**Root**
- `styles.css` — the single entry point consumers link. `@import` lines only.
- `readme.md` — this file.
- `SKILL.md` — agent-skill front matter for use outside this project.
- `thumbnail.html` — the system's homepage tile.
- `_dev_shim.js` — development fallback that lets any page here open standalone before the bundle is compiled. Not part of the delivered system; consumers can ignore it.

**`tokens/`** — `fonts.css`, `colors.css`, `typography.css`, `spacing.css`, `borders.css`, `elevation.css`, `motion.css`, `base.css` (element resets plus the `.tp-label`, `.tp-micro`, `.tp-num`, `.tp-prose`, `.tp-lead`, `.tp-rule`, `.tp-page` helpers).

**`components/`** — `components.css` imports one stylesheet per group and ships via `styles.css`. Each component is `<Name>.jsx` + `<Name>.d.ts` + `<Name>.prompt.md`, with one `@dsCard` per directory.

| Group | Components |
| --- | --- |
| `core/` | **Icon**, **Button**, **IconButton**, **Tag**, **Badge**, **Eyebrow** |
| `forms/` | **Field**, **Input**, **Select**, **Checkbox**, **Radio**, **Switch**, **Slider** |
| `surfaces/` | **Panel**, **Figure**, **Callout**, **Quote**, **Footnote**, **FootnoteList**, **EmptyState** |
| `navigation/` | **Tabs**, **Breadcrumb**, **Toc** |
| `data/` | **PlotFrame**, **StatTile**, **DataTable**, **ModelTable**, **DensityPlot**, **ForestPlot**, **ScatterBands** |
| `feedback/` | **Tooltip**, **Dialog** |

No source defined a component inventory, so this is a standard primitive set sized to the brand. *Intentional additions:* **Icon** (a wrapper for the substituted Phosphor set, so glyph usage stays in one place); **Eyebrow** (the uppercase-plus-hairline section marker the editorial layout depends on); **Footnote**/**FootnoteList** and **Quote** (editorial furniture); **StatTile**, **ModelTable**, **PlotFrame**, **DensityPlot**, **ForestPlot**, **ScatterBands** (the four data-viz families the brief named, plus their shared axis frame). `Panel` stands in for the conventional Card. There is no Toast, Avatar, Accordion or Progress — nothing in the brief needed one.

**`guidelines/`** — 22 specimen cards: `color-*` (ink ramp, teal, data series, surfaces, contrast), `type-*` (display, headings, body, numerals, labels, scale, tracking), `space-*` (scale, rhythm, sizes, grid), `brand-*` (wordmark, rules & radii, elevation, motion, icons, voice, plot rules), plus shared `card.css`.

**`slides/`** — six sample slide types at 1280×720: `01-title`, `02-section` (ink ground), `03-statement`, `04-figure`, `05-comparison`, `06-takeaways`, plus shared `slide.css`.

**`templates/`** — starting files a consuming project copies. Each is a folder with a `<Name>.dc.html` entry and a sibling `ds-base.js` (edit its one `base` line to point at the bound design system).

| Template | Entry | For |
| --- | --- | --- |
| **Research report** | `templates/research-report/` | Printable model report — running header/footer, abstract, method, captioned posterior figures, parameter and results tables, references, appendix on a new page. Built on `<doc-page>`, so PDF export needs no extra work. Tweaks toggle the abstract, parameter table, references and appendix. |
| **Talk deck** | `templates/talk-deck/` | Six-slide conference deck on `<deck-stage>` at 1280×720, matching the slide specimens. |

**`ui_kits/`**
- `personal_site/` — home, work, project write-up, publications, notes, post, about. Click-through. See its `README.md`.
- `posterior_explorer/` — an interactive model view with live sliders and real conjugate maths. See its `README.md`.

**`assets/`** — see `assets/README.md`. No marks; nothing to copy in yet.
