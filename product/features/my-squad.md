# My Squad — Foozi Product Spec

**Version:** 1.0  
**Status:** Design-Ready  
**URL Pattern:** `/my-squad` + CTAs on `/player/{slug}` + `/team/{slug}`  
**Phase:** MVP Phase 2 — Teams & Players

---

## Purpose

My Squad is a personal football management layer built on top of Foozi's player and club data. It combines a Watchlist (track players and their value) with a Fantasy element (build your own XI on a pitch). Tactra evaluates your squad like a real team. The feature lives on its own page but is fed from CTAs on every Player and Club Page.

---

## Design Principles (applied)

- **Zero friction entry** — add players from Player Page or Squad Galaxy with one tap
- **Works without login** — localStorage for guests, DB sync for registered users
- **Tactra as glue** — Squad Score calculated live from your selection
- **Social hook** — shareable squad URL drives organic growth
- **Mobile-first** — optimized for one-handed use

---

## Page Structure

```
/my-squad
│
├── HERO (Squad name, Tactra Score orb, key stats bar)
├── TAB NAV
│   ├── Squad (Pitch builder + Alerts + Share)
│   ├── Tracker (MV sparkline + per-player value)
│   ├── Tactra (Squad-Score + Stärken/Risiken)
│   └── VS Team (My Squad vs. real club comparison)
```

---

## Entry Points (CTAs)

### Player Page CTA
| Element | Description | Status |
|---|---|---|
| Hero button | `+ Zu meinem Squad` — green, below MUST HAVE badge | Designed |
| State toggle | If already in squad → `✓ Im Squad` (muted, removable) | Planned |
| Feedback | Toast notification on add: "Sané zu deinem Squad hinzugefügt" | Planned |

### Club Page — Squad Galaxy CTA
| Element | Description | Status |
|---|---|---|
| Node tap | Tap player node → bottom sheet with player info | Planned |
| Bottom sheet | Name · Position · MV · Form + `+ Zu Squad` button | Planned |
| Already added | Node shows green ring + checkmark if in squad | Planned |

---

## Hero

| Element | Description | Status |
|---|---|---|
| "MS" background | Large faded typographic element top-right | Designed |
| Page label | FOOZI · MEIN SQUAD | Designed |
| Squad name | "My Squad" — editable later | Designed |
| Meta strip | X/11 Spieler · Ø Form · Alert count | Designed |
| Tactra Score Orb | Animated, calculated from squad avg form | Designed |
| Key Stats Bar | Spieler · Gesamt-MV · Ø Form · Alerts | Designed |

---

## Tab: Squad

Core tab. Pitch builder + alerts + share.

### Alert Panel
| Element | Description | Status |
|---|---|---|
| Alert cards | One row per player with active alert | Designed |
| Alert types | Verletzung (red) · Formeinbruch (amber) | Designed |
| Pulsing dot | Animated dot per alert row | Designed |
| Panel visibility | Only shown when alerts > 0 | Designed |

### Squad Builder (Pitch)
| Element | Description | Status |
|---|---|---|
| Pitch background | SVG lines: penalty areas, center circle | Designed |
| Player nodes | Positioned by formation slot | Designed |
| Node size | Proportional to market value | Designed |
| Form ring | Green ≥7.5 · Amber 6.5–7.5 · Red <6.5 | Designed |
| Alert badge | Pulsing red/amber dot top-right of node | Designed |
| Remove | Tap node → removes from squad | Designed |
| Empty slot hint | "+ X Spieler hinzufügen" shown when <11 | Designed |
| Float animation | Staggered per player | Designed |
| Formation switcher | 4-3-3 / 4-2-3-1 / 3-5-2 | Planned |

### Add Player Panel
| Element | Description | Status |
|---|---|---|
| + Spieler button | Toggles panel open/closed | Designed |
| Available list | Players not yet in squad, from Foozi DB | Designed |
| Player row | Number · Name · Pos · Club · MV · Form | Designed |
| Tap to add | Immediately adds to pitch | Designed |
| Search / filter | Search by name or filter by position | Planned |

### Share
| Element | Description | Status |
|---|---|---|
| Share card | Green gradient card with squad URL | Designed |
| URL format | `foozi.de/squad/{slug}` | Designed |
| Share button | Native share sheet on mobile | Designed |
| Auth gate | URL only generated for logged-in users | Planned |

---

## Tab: Tracker

Market value history and per-player breakdown.

| Element | Description | Status |
|---|---|---|
| MV Sparkline | Animated area chart, last 6 months | Designed |
| Total value | Large number, +delta since start | Designed |
| Player MV list | Sorted by value descending | Designed |
| Bar per player | Proportional bar, alert color if flagged | Designed |
| Alert badges | "Verletzt" / "Form↓" inline | Designed |
| Historical data | Per-player MV per month | Planned |

---

## Tab: Tactra

AI evaluation of your squad.

| Element | Description | Status |
|---|---|---|
| Squad-Score hero | Orb + tier label + player count | Designed |
| Tier labels | STARK / SOLIDE / AUFBAUEN (threshold TBD) | Designed |
| Summary grid | Ø Form · Gesamt-MV · Alerts | Designed |
| Stärken rows | Auto-generated from squad data | Designed |
| Risiken rows | Alert-based + weakness detection | Designed |
| Full AI analysis | Natural language squad assessment | Planned |

---

## Tab: VS Team

Compare your squad against a real Bundesliga club.

| Element | Description | Status |
|---|---|---|
| My Squad card | Green, Score + MV | Designed |
| Real team card | Blue, Score + MV, selectable | Designed |
| VS label | Center divider | Designed |
| Comparison rows | Tactra Score · Ø Form · Marktwert · Top-Form Spieler | Designed |
| Dual bars | Green (mine) vs Blue (real), animated | Designed |
| Winner highlight | Bold color on winning side per row | Designed |
| Team selector | Switch comparison team | Planned |

---

## Data & State Architecture

### Squad Store (3 tasks — see GSD)

#### Task 1 — my-squad-store
Central state management for the squad.

```typescript
interface SquadStore {
  players: Player[]
  addPlayer: (player: Player) => void
  removePlayer: (id: string) => void
  clearSquad: () => void
  isInSquad: (id: string) => boolean
}
```

**Storage strategy:**
- Guest → `localStorage` key: `foozi_squad`
- Logged in → sync to user DB on every mutation
- Optimistic updates — UI updates immediately, DB syncs in background

**Tech:** Zustand (already in stack) recommended. Falls back gracefully if localStorage unavailable.

#### Task 2 — my-squad-cta
Reusable CTA component used on Player Page and Club Page.

```typescript
// Player Page usage
<AddToSquadButton player={player} />

// Club Page Squad Galaxy usage  
<PlayerNode player={player} showAddCTA />
```

**Button states:**
- Default → `+ Zu meinem Squad` (green)
- In squad → `✓ Im Squad` (muted green, click removes)
- Loading → spinner
- Disabled → squad full (11 players)

**Toast feedback:** On add/remove, show 3s toast bottom of screen.

#### Task 3 — my-squad-auth
Auth gate for sync and sharing features.

**Unauthenticated:**
- Squad works fully via localStorage
- Share button → prompts login: "Erstelle ein kostenloses Konto um deinen Squad zu teilen"
- MV history limited to session

**Authenticated:**
- Squad synced to DB
- Share URL generated: `foozi.de/squad/{userId}/{squadSlug}`
- Full MV history persisted
- Push alerts enabled (future)

---

## Data Requirements

| Entity | Fields |
|---|---|
| SquadPlayer | id, name, shortName, position, number, club, marketValue, formRating, alert (injury/form/null) |
| SquadStore | players[], updatedAt, userId? |
| MvHistory | Per month: month label, totalValue |
| TachtraSquadScore | score, tier, strengths[], risks[] |
| ShareSquad | squadId, slug, userId, players[], createdAt |

---

## Push Alerts (Future)

| Alert Type | Trigger | Channel |
|---|---|---|
| Verletzung | Player marked injured in data feed | Push + in-app badge |
| Formeinbruch | Form drops below 6.5 | Push + in-app badge |
| Marktwert↑ | MV increases >10% | Push + in-app badge |
| Nächstes Spiel | Player's club plays within 24h | Push |

---

## Tech Notes

- **State:** Zustand store (`useSquadStore`)
- **Persistence:** localStorage (guest) + Supabase/DB (auth)
- **Auth:** SSO / OAuth — existing Foozi auth system
- **Share:** Unique slug generation server-side
- **Mobile:** Bottom sheet for Galaxy CTA, native share API for sharing
- **Error boundaries:** Per module

---

## Innovation vs. Competitors

| Feature | Fantasy Bundesliga | Transfermarkt | Foozi |
|---|---|---|---|
| Pitch builder | Basic | — | Squad Galaxy with MV + Form |
| AI squad rating | — | — | Tactra Squad-Score |
| MV tracking | — | Manual | Automatic sparkline |
| vs Real team | — | — | Tactra comparison |
| Alert system | Injuries only | — | Injury + Form + MV |
| Share squad | Yes | — | URL + native share |

---

## Status Summary

| Tab / Feature | Items | Designed | Planned | Open |
|---|---|---|---|---|
| Entry CTAs | 6 | 2 | 4 | 0 |
| Hero | 6 | 6 | 0 | 0 |
| Squad tab | 12 | 9 | 3 | 0 |
| Tracker tab | 7 | 5 | 2 | 0 |
| Tactra tab | 6 | 5 | 1 | 0 |
| VS Team tab | 7 | 6 | 1 | 0 |
| Squad Store | 3 | 0 | 3 | 0 |
| Push Alerts | 4 | 0 | 0 | 4 |
| **Total** | **51** | **33** | **14** | **4** |

---

## GSD Checklist

- [ ] my-squad-store — Zustand store, localStorage + DB sync
- [ ] my-squad-cta — AddToSquadButton component (Player Page + Club Page)
- [ ] my-squad-auth — Auth gate for share + sync
- [ ] my-squad-page — Full page: Hero + 4 tabs
- [ ] my-squad-alerts — Alert badge system + push (future)
- [ ] my-squad-share — Share URL generation + native share

---

## Related Files

- `product/features/player-page.md` — Player Page spec (entry point)
- `product/features/club-page.md` — Club Page spec (entry point)
- `CLAUDE.md` — platform overview and design tokens

---

*Foozi · fussballdaten.de · My Squad Spec v1.0*
