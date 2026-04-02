# Dungeon Crawler Carl — Stat Tracker

**Live app:** https://rdsciv.github.io/dcc-stat-tracker/

An interactive character tracker for Carl and Princess Donut from Matt Dinniman's *Dungeon Crawler Carl* series. Track their stats, skills, spells, gear, and passive effects as they progress through the dungeon.

---

## Features

- **Page Lookup** — Enter a book number and page and jump to exactly where Carl and Donut are at that moment
- **Stats** — Radar charts + stat pills with color-coded highlights showing what changed (and in which direction)
- **Skills** — Combat, dungeon crawling, explosives, vehicle, and other skills with levels and notes. New acquisitions flagged with 🆕
- **Spells** — Full spell list with levels
- **Gear** — Every equipment slot with item descriptions and enchantment details
- **Passives & Buffs** — Passive effects, resistances, memberships, and debuffs from gear and tattoos
- **Timeline scrubber** — Drag through every stat change point across Books 1–2

---

## Data Coverage

| Book | Carl | Donut |
|------|------|-------|
| Book 1 (Floor 1) | ✅ Full | ✅ Full |
| Book 2 (Floor 2) | ✅ Stats + class | ✅ Stats + spells |
| Book 3 (Floor 4) | ✅ 4 snapshots (pp. 36–506) | ✅ 3 snapshots (pp. 36–506) |
| Book 4+ | ❌ Not yet added | ❌ Not yet added |

All data sourced from [dungeon-crawler-carl.fandom.com](https://dungeon-crawler-carl.fandom.com). Stats are verified against the wiki's chapter-by-chapter tracking tables.

**Note:** Carl's STR shows base / equipped (✦) values from page 199 onward due to the War Gauntlet of the Exalted Grull.

---

## Stack

Single `index.html` — no build step, no dependencies beyond:
- [Chart.js](https://www.chartjs.org/) (radar charts)
- Google Fonts (Bebas Neue, Rajdhani, Share Tech Mono)

Data scraped from the fandom wiki using [Scrapling](https://github.com/D4Vinci/Scrapling) to bypass Cloudflare protection.

---

## Contributing

If you spot a stat error or want to add Book 3+ data, open a PR. The data lives directly in the `<script>` block in `index.html` as `CARL_SNAPSHOTS` and `DONUT_SNAPSHOTS` arrays. Each entry looks like:

```js
{
  page: 199, book: 1, level: 9, cls: 'Human',
  str: 9, int: 3, con: 12, dex: 6, chr: 4, str2: 12, // str2 = with gauntlet
  event: 'Description of what happened at this page',
  combatSkills: [{ name: 'Iron Punch', lvl: '5 (7✦)', note: 'Gauntlet +2' }],
  spells: [],
  gear: [{ slot: 'Wrists (R)', item: 'War Gauntlet of the Exalted Grull' }],
  passives: ['Gauntlet — 2% stun on hit'],
}
```

---

## Usage Tips

- **Page Lookup:** Enter any page number and the tracker snaps to the nearest snapshot at or before that page — great for following along as you read
- **Timeline scrubber:** Drag the slider to sweep through every stat change point chronologically
- **Color-coded stats:** Green = increased since last snapshot, red = decreased, white = unchanged
- **🆕 badge:** Flags skills or spells newly acquired at that snapshot

---

## Roadmap

- [ ] **Book 4+ data** — Floors 5–8 stats, skills, and gear
- [ ] **Donut companion sheet** — Dedicated view for Donut's full skill and spell tree
- [ ] **Mobile layout** — Responsive improvements for small screens
- [ ] **Search** — Filter skills/spells by name across all snapshots

---

*You will not break me. You will not fucking break me.* — Carl

---

## Changelog

| Date | Change |
|------|--------|
| 2026-04-02 | Added roadmap section — Book 4+ data, Donut companion sheet, mobile layout improvements |
| 2026-04-01 | Added Usage Tips section to README — page lookup, timeline scrubber, color-coded stats, 🆕 badge explained |
| 2026-03-31 | Added contributing note: each snapshot entry schema documented inline with str2/equipped stat fields |
| 2026-03-30 | Clarified data coverage table: Book 3 has 4 Carl + 3 Donut snapshots; Book 4+ noted as not yet added |
| 2026-03-30 | Added changelog section; noted Chart.js + Google Fonts as only external deps |
| 2026-03-20 | Initial release — Books 1–3 stat data, radar charts, timeline scrubber |
