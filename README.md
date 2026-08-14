<div align="center">

# ⛏️ Clash of Clans Datamine

**Automated, unfiltered patch notes — pulled straight from Supercell's asset CDN the moment a new build ships.**

[![Last update](https://img.shields.io/github/last-commit/NotAmti/Clash-of-Clans-Datamine?style=flat-square&label=last%20update&color=f6c343&labelColor=1a1a1a)](../../commits/main)
[![Reports](https://img.shields.io/github/directory-file-count/NotAmti/Clash-of-Clans-Datamine/reports?style=flat-square&label=reports&color=4caf50&labelColor=1a1a1a)](reports/)
[![Data source](https://img.shields.io/badge/source-Supercell%20CDN-0d47a1?style=flat-square&labelColor=1a1a1a)](#how-it-works)
[![Automated by](https://img.shields.io/badge/automated%20by-Discord%20bot-5865F2?style=flat-square&logo=discord&logoColor=white&labelColor=1a1a1a)](#how-it-works)

</div>

---

No teasers, no marketing copy — just the numbers Supercell actually shipped. A Discord bot watches for new Clash of Clans releases, pulls the raw game-data files out of each one, and diffs them against the last known snapshot. What comes out is checked into [`reports/`](reports/): every new unit, every level added, every stat nudged up or down.

## How it works

```mermaid
flowchart LR
    A[📡 Poll APKPure] -->|new version found| B[⬇️ Pull release]
    B --> C[🔑 Extract CDN fingerprint]
    C --> D[📊 Fetch game-data CSVs]
    D --> E[🔍 Diff vs. last snapshot]
    E -->|changes found| F[📝 Publish report]
    F --> G[🔔 Discord alert]
    A -->|no change| A
```

The bot checks for a new release on a fixed interval. When one appears, it pulls the game's asset fingerprint, fetches every tracked data category from Supercell's CDN, and diffs the new snapshot against the previous one. Anything that changed gets written here as a self-contained markdown report and pinged out to Discord.

## What gets tracked

<table>
<tr><td valign="top">

**Home Village**
- ⚔️ Troops
- 🦸 Heroes
- 🐾 Pets
- 🔮 Spells
- 🛡️ Equipment
- 🏛️ Buildings
- 🎨 Skins
- 💣 Traps
- 🏆 Achievements
- 🌳 Decorations
- 🏰 Town Hall levels

</td><td valign="top">

**Clan Capital**
- 🗿 Troops
- 🏯 Buildings
- 🌆 Decorations
- 🗺️ Districts
- 🪨 Obstacles
- 💥 Spells
- 🧨 Traps

</td><td valign="top">

**Leagues & Progression**
- 🎖️ Leagues
- 🥈 Leagues (Versus)
- 🏅 War Leagues
- 🎗️ League Tiers
- 🏳️ Alliance Badges
- 🎫 Pass Tasks
- 📦 Collection Items

</td></tr>
</table>

26 categories in total, each diffed independently every run.

## Reading a report

Every file in [`reports/`](reports/) is named `YYYY-MM-DD_<fingerprint>.md` and opens with a scoreboard:

| New units | Balance changes | Bulk rollouts |
|---|---|---|
| 0 | 50 | 2 |

Below that, one section per category that actually changed — new units with their headline stats, level-by-level stat tables, and **bulk rollouts**: the same exact value swap applied across dozens of entries at once, which usually means a global mechanic change rather than individual balance tuning. Nothing is truncated; this is the full diff, not a highlight reel.

## Why this exists

Clash of Clans patch notes are often vague or delayed. The raw game-data CSVs Supercell ships in every build aren't — they're the literal numbers the client runs on. This repo just makes them visible, automatically, the moment they change.

---

<div align="center">

*Fan-made and unofficial. Not affiliated with, endorsed by, or associated with Supercell.*

</div>
