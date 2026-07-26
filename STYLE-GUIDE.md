# Style Guide — nayanprakash.com v2 ("The Growth Report")

The contract for anyone (human or AI model) editing or extending the v2 site. Rules here win over any editing instinct. The v1 editorial site in the parent folder has its own guide; the two systems never mix.

## Concept

An annual report on the operator. The site reads like a beautifully typeset performance report about Nayan's career: chart-paper ground, audited figures with cited sources, a career trajectory chart as the hero device, and accounts framed as portfolio holdings with returns. Case studies are lab-note-style: Hypothesis, Method, Result, because the operator diagnoses before he rebuilds.

Single committed light theme. Do NOT add a dark mode.

## Tokens (`v2/css/style.css`, `:root`)

| Token | Value | Use |
|---|---|---|
| `--paper` | `#FDFDFC` | Page ground (with `--grid` chart-paper lines at 56px) |
| `--card` | `#FFFFFF` | Report surfaces: panels, tiles, tables |
| `--ink` | `#16211C` | Primary text (green-biased near-black), heavy rules |
| `--muted` | `#5D6B63` | Secondary text |
| `--green` | `#0B6B4F` | Growth accent: stats, returns, buttons, links, curve |
| `--green-deep` | `#0E3B2C` | Closing band ground |
| `--amber` | `#B9821D` | Section numbers (SEC. NN), HMR labels, current-position marker, auditor's-note top borders |
| `--line` | `#DCE2DE` | Card borders, hairlines |
| `--ivory` | `#F2EFE6` | Text on green-deep |

Rule of thumb: **green is growth and action; amber is annotation and "you are here."** Never swap them.

## Typography

- Display: **Source Serif 4** (Google Fonts). Fallbacks: Iowan Old Style, Palatino, Georgia.
- Figures, labels, captions, nav: **IBM Plex Mono**, uppercase with 0.1 to 0.16em letter-spacing.
- Body: system sans stack.
- Numbers in tiles and tables: `font-variant-numeric: tabular-nums`.

## Signature devices

1. **Report framing**: masthead carries "Performance Report · FY2019–2026"; figures get mono captions (`Fig. 01 —`); sections are numbered `SEC. NN` in amber.
2. **Career trajectory chart** (homepage): SVG curve with milestone dots; every dot is a link (`<a>` in SVG) with a `<title>` tooltip. The amber dot is always the current position. When the story advances, extend the curve, don't redraw history.
3. **KPI tiles** (`.kpi`): white card, 3px green top border, serif green number, mono label. Followed by a `.footnote` citing data sources.
4. **Portfolio table** (`.portfolio`): four data columns (Holding / Sector / Position / Return) plus arrow. Rows are clickable (`onclick`) and the holding name is a real `<a>` for accessibility.
5. **HMR case structure** (`v2/work/*.html`): every case page runs `01 · Situation`, `02 · Hypothesis`, `03 · Method`, `04 · Result` as amber mono labels (`.hmr`) over serif h2s. The hypothesis must be falsifiable and must acknowledge what the old strategy got right; the result states whether the hypothesis held.
6. **Finding callout** (`.finding`): the one-sentence takeaway, serif on `--green-soft` with a green left border. One per case page, placed after Method.
7. **Auditor's notes** (`.rec-card`): recommendation cards with amber top borders, grayscale avatars from `../assets/images/people/`, verbatim quotes only.
8. **Closing band** (`.band`): deep green panel with ivory text and amber primary button. The only dark surface on the site; do not add others.

## Layout

- Container 1080px; section rhythm via `--section-gap`.
- Everything raised sits on a `.panel`-style white card with `--shadow`; the chart-paper ground shows between cards.
- Wide tables wrap in `.table-scroll` (`overflow-x: auto`); the page never scrolls sideways.
- Breakpoints: 900px and 600px.

## Content rules (identical to v1, non-negotiable)

- No em dashes (—) anywhere. No fabricated numbers, quotes, or logos; missing material is marked `[INSERT ...]` / `[ADD ...]`.
- No AI-marketing vocabulary (seamless, leverage, cutting-edge, unlock, elevate, robust, innovative...). Plain verbs.
- No staccato triplets, no pre-answered objections, no significance-label closers.
- Every claim pairs a number with its mechanism.
- Recommendations are verbatim; trimming may only cut whole sentences.

## Shared assets

v2 reuses the parent folder's `assets/` (portraits, people photos): paths are `../assets/...` from v2 pages and `../../assets/...` from `v2/work/`. No resume link anywhere on v2 (removed July 2026); do not reintroduce one. Client logos and tool chips load from Google's favicon service with `onerror` hiding, same pattern as v1.

## Page anatomy

Every page: masthead (wordmark + report subtitle + mono nav + green CTA) → main → footer (mono colophon). Case pages: crumb → story-head (eyebrow `Holding NN · sector · period`, serif H1, dek) → 3 KPI tiles → story-grid (HMR body + sticky factbox) → prev/next loop (01→...→07→01). To add a holding: copy a case page, renumber, add a portfolio table row, fix the neighbors' prev/next.
