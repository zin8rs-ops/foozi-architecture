# Player Page — Foozi Product Spec

**Version:** 1.0  
**Status:** Design-Ready  
**URL Pattern:** `/player/{slug}`  
**Phase:** MVP Phase 2 — Teams & Players

---

## Purpose

The Player Page is a comprehensive profile for individual football players. It combines data-first statistics with AI-powered insights (Tactra) and engaging, game-inspired UI elements. The page is designed to be the most informative and visually distinctive player profile in German-language football media.

---

## Design Principles (applied)

- **Data first** — scores, stats, and ratings always visible above the fold
- **Tactra as differentiator** — AI-powered Verdict and DNA are unique to Foozi
- **Gaming-engaged** — animated reveals, flip interactions, score rings
- **Mobile-first** — all layouts scale from mobile up
- **Token-driven** — Foozi design tokens throughout, no hardcoded values

---

## Page Structure

```
/player/{slug}
│
├── HERO (always visible)
├── TAB NAV
│   ├── Übersicht
│   ├── Statistiken
│   ├── Tactra
│   ├── Spiele
│   ├── Karriere
│   └── My Squad
```

---

## Hero

Always visible above the tab navigation. Never scrolls away.

| Element | Description | Status |
|---|---|---|
| Trikotnummer | Large typographic background element (opacity 4%), positioned top-right | Designed |
| Player Identity | Name (large, bold), Position badge, Club · League · Season | Designed |
| Meta Info | Nation · Age · Height · Strong Foot | Designed |
| Key Stats Bar | 4 animated counters: Tore · Vorlagen · Spiele · Note | Designed |
| Tab Navigation | Sticky tab bar directly beneath hero | Designed |

**Key Stats animate on page load** (count up from 0 to value, 800ms duration).

---

## Tab: Übersicht

Landing tab. Overview of the most important player signals at a glance.

### Tactra Gauge
| Element | Description | Status |
|---|---|---|
| Arc gauge | Win probability: Mit / Ohne player comparison | Designed |
| Influence badge | `+87 Einfluss` badge, green accent | Designed |
| Mit/Ohne grid | Side-by-side H/D/A breakdown | Designed |

### Form Strip
| Element | Description | Status |
|---|---|---|
| Last 10 chips | S/U/N colored chips with opponent abbreviation | Designed |
| Goal/Assist badges | Inline T/A badges per chip | Designed |
| Hover tooltip | Score, result, scoreline on hover | Designed |

### Marktwert Sparkline
| Element | Description | Status |
|---|---|---|
| Mini line chart | Last 5 seasons market value trend | Designed |
| Current value | Prominent display above chart | Designed |

### Radar Chart
| Element | Description | Status |
|---|---|---|
| 6-attribute polygon | Tempo · Abschluss · Passen · Dribbling · Verteidigung · Physis | Designed |
| Liga-Ø reference | Gray fill showing league average | Designed |
| Animated fill | Polygon animates in on tab load | Designed |

---

## Tab: Statistiken

Two sub-views selectable via segment control: **Percentile** and **Duell**.

### Percentile View
| Element | Description | Status |
|---|---|---|
| Animated rings | SVG ring per stat, fills on load | Designed |
| Color tiers | Elite (green) · Stark (blue) · Solide (amber) · Schwach (red) | Designed |
| Grouped sections | Offensiv · Kreativität · Physis | Designed |
| Tier badge | Inline badge per stat row | Designed |

**Stats included:** Tore · Vorlagen · xG · xA · Schüsse/Sp. · Schlüsselpässe/Sp. · Dribbles/Sp. · Passquote % · km/Sp. · Pressingaktionen

### Duell View (Comparison Tool)
| Element | Description | Status |
|---|---|---|
| VS screen | Green card (Sané) vs Blue card (opponent) | Designed |
| Opponent selector | Dropdown — selectable from Bundesliga pool | Designed (basic) |
| Animated dual bars | Bars animate toward each other on load | Designed |
| Win-count bar | Full-width bar: categories won left vs right | Designed |
| Category label | `X Kategorien gewonnen` per side | Designed |
| Expanded player pool | Connect to full player database | Planned |

---

## Tab: Tactra

AI-powered player evaluation. Foozi's key differentiator. Split into 4 sub-views.

### Verdict (sub-view 1)
| Element | Description | Status |
|---|---|---|
| Score orb | Animated SVG ring, counts 0→score on load | Designed |
| Tier label | GAMECHANGER / SOLID / ROTATION / BENCH | Designed |
| MUST HAVE badge | Pulsing green badge | Designed |
| KI-Analyse text | AI-generated natural language summary | Ready |
| Stärken rows | Percentile value + mini bar + text per strength | Designed |
| Risiken rows | Red card rows with risk description | Designed |

### DNA Cards (sub-view 2) — Sorare-Style
| Element | Description | Status |
|---|---|---|
| 3×2 card grid | Aspect-ratio 3:4 cards | Designed |
| Flip interaction | Tap flips card to color + description | Designed |
| Score ring | Animated SVG ring per card | Designed |
| Rank badge | Top 7% / Liga-Ø / Schwäche | Designed |
| Shimmer lines | Top + bottom shimmer accent | Designed |
| Vergleichsprofile | Historical player comparisons below grid | Designed |

**Default DNA attributes:** Elite Dribbler · Chance Creator · Direktspieler · Volume Shooter · Presser · Luftspiel

### Impact (sub-view 3)
| Element | Description | Status |
|---|---|---|
| Mit/Ohne bars | Dual bar rows per metric | Designed |
| Diff badge | `+14%` green badge per row | Designed |
| Summary grid | 3-cell summary: Mehr Siege · Mehr Tore · Mehr Chancen | Designed |

**Metrics:** Siegrate · Tore/Sp. · Chancen/Sp. · xG/Sp.

### Transfer (sub-view 4)
| Element | Description | Status |
|---|---|---|
| Marktwert card | Transfermarkt market value | Designed |
| Tactra Spielerwert | AI-calculated player value with Tactra badge | Designed |
| Verdict badge | UNTERBEWERTET / FAIR / ÜBERBEWERTET | Designed |
| Delta value | Large `+38%` statement number | Designed |
| Disclaimer | Data source note | Designed |

---

## Tab: Spiele

Match history for the current season.

| Element | Description | Status |
|---|---|---|
| Match rows | S/U/N badge · Opponent · Score · Goals · Assists · Rating | Designed |
| Rating color | Green ≥8 · Default 6–8 · Red <6 | Designed |
| Filter bar | All · Siege · Niederlagen · Assists | Planned |
| Season switcher | Switch between seasons | Planned |

---

## Tab: Karriere

Career timeline with market value context per club.

| Element | Description | Status |
|---|---|---|
| Timeline dots | Dot + vertical line connector per club | Designed |
| Club card | Club · Period · Apps · Goals · Goals/Game | Designed |
| Marktwert per station | Value display + career-high bar indicator | Designed |
| Career-high label | `Karrierehoch` badge on peak value | Designed |
| Nation badges | International career stations | Planned |

---

## Tab: My Squad

Feature scope TBD. Connects player profile to personal squad/watchlist.

| Element | Description | Status |
|---|---|---|
| Add to Squad CTA | `+ Zu meinem Squad hinzufügen` button | Open |
| Watchlist connection | Save player to watchlist | Open |
| Fantasy connection | Add to fantasy team | Open |
| Squad scope | Fantasy vs. Watchlist — to be defined | Open |

> **Note:** My Squad feature scope to be defined as a separate GSD Milestone.

---

## Data Requirements

| Entity | Fields |
|---|---|
| Player | id, name, slug, number, position, positionCode, club, league, nation, age, height, foot |
| Season Stats | goals, assists, matches, rating, minutes, xG, xA, passAcc, dribbles, shots, keyPasses, kmPerGame, pressures, aerials |
| Percentile | Per stat: percentile rank vs. position group in league |
| Form | Last N matches: opponent, result, score, goals, assists, rating |
| Career | Per club: name, period, apps, goals, marketValue |
| Market Value | Per season: season label, value in Mio. € |
| Tactra | score, tier, verdict, withStats (H/D/A %), withoutStats, influenceScore, transferValue |
| DNA | Per attribute: label, score, rank, description, color |

---

## Tech Notes

- **Framework:** React + TypeScript + Vite + Tailwind CSS
- **Animations:** motion.dev for page transitions, CSS keyframes for bar/ring animations
- **Data:** All via typed hooks — no direct data.ts imports
- **Config-driven:** Player data fully decoupled from UI components
- **Error boundaries:** Per module — no white-screen crashes

---

## Status Summary

| Tab | Modules | Designed | Ready | Planned | Open |
|---|---|---|---|---|---|
| Hero | 4 | 4 | 0 | 0 | 0 |
| Übersicht | 4 | 4 | 0 | 0 | 0 |
| Statistiken | 2 | 2 | 1 | 1 | 0 |
| Tactra | 4 | 4 | 1 | 0 | 0 |
| Spiele | 1 | 1 | 0 | 2 | 0 |
| Karriere | 1 | 1 | 0 | 1 | 0 |
| My Squad | 1 | 0 | 0 | 0 | 4 |
| **Total** | **17** | **16** | **2** | **4** | **4** |

---

## Related Files

- `.product-design-system/platform-pages.md` — page type registry
- `.product-design-system/mvp-roadmap.md` — Phase 2 context
- `foozi-architecture-overview.md` — repository structure
- `CLAUDE.md` — platform overview and design tokens

---

*Foozi · fussballdaten.de · Player Page Spec v1.0*
