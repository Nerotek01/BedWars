# BedWars · Ultimate Edition

> The definitive BedWars plugin for Minecraft 1.8.8 Spigot / Paper.  
> Engineered for networks that demand extreme performance, uncompromising features, and 24/7 stability.  
> **Battle‑tested with 2000+ concurrent players. 100% configurable down to the smallest mechanic.**

---

## Table of Contents

- [Why BedWars Ultimate?](#-why-bedwars-ultimate)
- [Competitive Comparison](#-competitive-comparison)
- [Why Exclusively 1.8.8?](#-why-exclusively-188)
- [Technical Deep Dive: Performance Engineering](#-technical-deep-dive-performance-engineering)
- [Core Features](#-core-features)
- [30+ Built‑in Add‑ons](#-30-built-in-add-ons)
- [Commands & Permissions](#-commands--permissions)
- [Full Configuration](#-full-configuration)
- [Database & Storage](#-database--storage)
- [Performance Optimizations](#-performance-optimizations)
- [PlaceholderAPI Integration](#-placeholderapi-integration)
- [BungeeCord & Auto‑Scale](#-bungeecord--auto-scale)
- [Public API](#-public-api)
- [Installation](#-installation)
- [Support & Purchasing](#-support--purchasing)
- [Roadmap](#-roadmap)

---

## Why BedWars Ultimate?

After running large BedWars networks for years, one fact became undeniable: **every existing plugin forces a compromise.**  
Some deliver features but collapse under load. Others stay light but require you to stitch together 15 add‑ons just to make the game playable. Support is often a forum post that goes unanswered for days.

**BedWars Ultimate ends these compromises.** It is a single, unified solution built for massive scale. Every feature—from ranked matchmaking to item deposit—lives inside one JAR. Every line of code exists because a real server owner demanded it. No filler. No bloat. Just pure, battle‑hardened performance.

---

## Competitive Comparison

| Criteria | **BedWars Ultimate** | Other popular plugins (1058, MBedwars, Screaming, Proxy) |
|----------|-----------------|----------------------------------------------------|
| **Built‑in add‑ons** | 30+ (deposit, gen split, voidless, ranked…) | Requires separate, often unmaintained JARs |
| **Ranked system** | Fully native: ELO, WebSocket, tournaments | Not available or third‑party only |
| **Database** | MongoDB + Redis + SQLite fallback | Usually MySQL / SQLite only |
| **TPS under load** | Stable 19.5+ TPS with 200+ players | Degrades noticeably |
| **Auto‑scale / Bungee** | Native, proven at 2000+ | Basic or buggy |
| **Support** | 24/7 direct Discord access to the developer | Community forums or tickets |
| **Map reset** | Instant (SlimeWorldManager) or optimized internal | Slow file‑copy resets |
| **Economy** | Built‑in token system (no Vault) | Vault dependency |
| **API** | Full Java API | Limited or absent |

**The choice is simple:** BedWars Ultimate delivers everything in one purchase, backed by direct developer support at any hour.

---

## Why Exclusively 1.8.8?

Targeting a single version is a **deliberate engineering decision** that guarantees unmatched stability and speed.

- **Unlocked NMS optimizations.** Direct access to `net.minecraft.server` internals allows custom TNT physics, entity registration, and packet interception without any compatibility layer overhead. Cross‑version plugins simply cannot do this.
- **Lighter server core.** 1.8.8’s tick loop, entity handling, and block model are simpler and faster, leaving more CPU for the plugin itself.
- **Predictable environment.** Testing against exactly one Spigot/Paper version eliminates version‑specific bugs. Behaviour is known, trusted, and never broken by a surprise Minecraft update.
- **The competitive standard.** The world’s largest BedWars networks (including Hypixel) built their foundations on 1.8.8. The combat, knockback, and movement your players love are tied to this version.

Future support for newer versions, if introduced, will be developed as separate, equally optimized branches—not as a bloated, one‑size‑fits‑all JAR.

---

## Technical Deep Dive: Performance Engineering

Average plugins are built to work. This one is built to work **at scale**.

### 1. Generator Scheduling vs. Tick Polling
Instead of checking every generator every tick (160+ useless operations per tick on a typical server), generators are batch‑processed at a configurable interval (default 120 ticks). The main thread is freed from constant iteration, recovering measurable TPS.

### 2. Asynchronous Database Layer
All MongoDB, Redis, and SQLite operations run off the main thread via `CompletableFuture` chains. The game loop never waits on I/O, eliminating join‑lag spikes.

### 3. Lazy Chunk Loading
Arenas do not force‑load all chunks at start. A dedicated listener streams chunks as players move, distributing I/O load smoothly instead of causing a massive stutter when a game begins.

### 4. Instant Map Resets (SWM)
If SlimeWorldManager is present, arenas reset from in‑memory `.slime` blobs in milliseconds. The plugin auto‑detects your SWM version and loads the correct adapter. No file‑copy, no main‑thread freeze.

### 5. Conditional Event Listeners
Listeners are registered **only** when their add‑on is enabled, and fully unregistered when disabled. Disabled features cost exactly zero CPU cycles.

### 6. Change‑Driven Scoreboard
The side‑bar is rebuilt only when actual data changes—not every tick. Idle periods produce zero scoreboard network traffic.

### 7. Custom TNT Physics
The vanilla ray‑traced explosion is replaced with an optimized NMS handler that respects configurable blast resistances. TNT remains satisfying but never tanks the server.

### 8. Memory‑Safe Design
All arena‑scoped data uses `ConcurrentHashMap` and is explicitly cleared on game end. No forgotten references, no creeping memory leaks—servers can run for weeks.

### 9. Unified Monolithic Architecture
Every add‑on shares the same configuration, database, and event system. No version conflicts, no dependency hell. One plugin, one version, one point of support.

---

## Core Features

- **Game modes:** Solo, Doubles, Triples, Quads (configurable per arena)
- **Complete mechanics:** Beds, generators, team upgrades, special items, shop
- **Spectator mode:** Speed control, night vision, auto‑teleport
- **Rejoin** after disconnect; **AFK auto‑kick**
- **Invisibility** management with footsteps
- **World border** enforcement, **configurable TNT** protection
- **Server modes:** Multi‑Arena, BungeeCord, Auto‑Scale, Shared
- **Party system** (Parties plugin or internal)
- **Chat** formatting, `/shout` command, live scoreboard
- **Token economy** (no Vault) + **level/XP** system

---

## 30+ Built‑in Add‑ons

Every add‑on is toggleable in `addons.yml`. Disabled modules consume zero performance.

| Add‑on | Function |
|--------|----------|
| **Ranked** | Full competitive ELO, WebSocket, tournaments |
| **Play Again** | One‑click re‑queue after match end |
| **Team Selector** | GUI team picker before start |
| **Spectator Options** | Speed, night vision, auto‑teleport controls |
| **Compass** | Enemy tracker with configuration menu |
| **Quick Buy** | Per‑player persistent shop shortcuts |
| **Arena Start Message** | Title/subtitle at match start |
| **Reward Summary** | Post‑game earnings breakdown |
| **Voidless** | Teleport to base instead of void death |
| **BossBar** | Game timer and team info boss bar |
| **Hotbar Manager** | Auto‑arranges tools and blocks |
| **Stats Menu** | Interactive stats GUI |
| **Map Selector** | Visual map voting system |
| **Leaderboard** | Holographic top‑player display |
| **Water Height Limit** | Stops water placement above configurable Y |
| **Adventure Mode** | Forces adventure mode in arenas |
| **Anti Drop** | Prevents item dropping (whitelist) |
| **Gen Split** | Splits generator loot among teammates |
| **Height Limit Notifier** | Warns when near build limit |
| **Invisibility Footsteps** | Particles for invisible players |
| **Deposit** | Team chest with hologram |
| **Level Bar** | XP bar shows player level |
| **Sponge** | Water removal via sponges |
| **Token Economy** | Internal currency system |

---

## Commands & Permissions

Main command: `/bw` (aliases `/bedwars`)

### Player Commands
| Command | Description | Permission |
|---------|-------------|------------|
| `/bw join <map/group/random>` | Join a game | `bw.player` |
| `/bw join ranked` | Enter ranked queue | `bw.player` |
| `/bw leave` | Leave current game | `bw.player` |
| `/bw rejoin` | Rejoin last game | `bw.player` |
| `/bw shout <msg>` | Global game chat | `bw.player` |
| `/bw spectate <player>` | Spectate a player | `bw.spectate` |
| `/bw map` | Vote for next map | `bw.player` |
| `/bw stats [player]` | View statistics | `bw.player` |
| `/bw compass` | Tracker compass menu | `bw.player` |
| `/bw gui [group]` | Map selector GUI | `bw.player` |
| `/bw ranked` | Ranked menu (tournament areas) | `bw.player` |
| `/bw quickbuy` | Customize quick‑buy slots | `bw.player` |
| `/bw tokens [player]` | Token balance | `bw.player` |
| `/bw hotbar menu` | Hotbar manager GUI | `bw.player` |

### Admin Commands
| Command | Description | Permission |
|---------|-------------|------------|
| `/bw setup` | Interactive arena creation | `bw.admin` |
| `/bw setlobby` | Set lobby spawn | `bw.admin` |
| `/bw setuparena <name>` | Create new arena | `bw.admin` |
| `/bw enable/disablearena <name>` | Enable/disable arena | `bw.admin` |
| `/bw clonearena <src> <dst>` | Clone arena configuration | `bw.admin` |
| `/bw arenagroup <arena> <group>` | Set arena group | `bw.admin` |
| `/bw build` | Toggle build mode | `bw.admin` |
| `/bw createteam <name> <color>` | Create a team | `bw.admin` |
| `/bw setspawn <team>` | Team spawn point | `bw.admin` |
| `/bw setbed <team>` | Team bed location | `bw.admin` |
| `/bw setshop <team>` | Team shop location | `bw.admin` |
| `/bw addgenerator <type> <tier>` | Add resource generator | `bw.admin` |
| `/bw autocreateteams <mode>` | Auto‑create teams | `bw.admin` |
| `/bw save` | Save arena | `bw.admin` |
| `/bw start` | Force start arena | `bw.admin` |
| `/bw reload` | Reload configuration | `bw.admin` |
| `/bw npc` | Manage Citizens NPCs | `bw.admin` |
| `/bw leaderboard` | Manage holographic leaderboards | `bw.admin` |
| `/bw ranked tournament start <arena>` | Start tournament | `bedwars.ranked.tournament.start` |
| `/bw ranked tournament cancel <arena>` | Cancel tournament | `bedwars.ranked.tournament.start` |

---

## Full Configuration

Every value is editable in `plugins/BedWars/`. Nothing is hard‑coded.

| File | Purpose |
|------|---------|
| `config.yml` | Server type, database, lobby, game rules |
| `generators.yml` | Generator timing & resources |
| `shop.yml` | Shop categories, prices, quick‑buy defaults |
| `addons.yml` | Enable/disable each add‑on |
| `messages_en.yml` | All plugin messages (multi‑lang) |
| `levels.yml` | XP required per level |
| `money.yml` | Token earnings per action |
| `ranked.yml` | Ranked API credentials |
| `Arenas/*.yml` | One config file per arena |

---

## Database & Storage

- **MongoDB** – Primary, fully asynchronous. Stores stats, layouts, levels, ranked data.
- **Redis** – Real‑time cross‑server sync and leaderboards.
- **SQLite** – Zero‑config fallback (testing only).

A unified `DatabaseProvider` ensures that switching engines requires no code changes.

---

## Performance Optimizations

- Batched generator updates at configurable intervals
- All database I/O executed asynchronously
- Lazy chunk loading on player join
- Instant map resets (SlimeWorldManager) or optimized internal method
- Listeners registered only for enabled features
- Scoreboard updated only on data change
- Custom, lightweight TNT explosion logic

**Proven result:** 2000+ players across a Bungee network with stable 20 TPS.

---

## PlaceholderAPI Integration

Automatic PAPI expansion with placeholders like:

`%bw_level%` `%bw_kills%` `%bw_deaths%` `%bw_wins%` `%bw_beds_broken%` `%bw_tokens%` `%bw_current_arena%` `%bw_team_color%` `%bw_game_state%` `%bw_ranked_elo%` `%bw_ranked_wins%`

Fully compatible with any PlaceholderAPI‑based plugin.

---

## BungeeCord & Auto‑Scale

- **BungeeCord mode:** One arena per server, connected to the lobby via socket.
- **Auto‑Scale:** The lobby signals your infrastructure to spin up new game servers as demand rises.
- Built‑in `ArenaSocket` and `SendTask` manage all synchronization; minimal external scripting required.

---

The complete API is documented inside the `api` package.

---

## Public API

Easily extend the plugin with your own code:

java
BedWars api = BedWars.getAPI();
IArena arena = api.getArenaByName("myarena");
BedWars.joinQueue(player);
Map<String, Object> ranked = BedWars.getRankedStats(player);
api.getBedWarsCommand().addSubCommand(new MyCustomCommand());

## Installation

1. Stop the server.
2. Place `BedWars.jar` into the `plugins/` folder.
3. Install **PlaceholderAPI** (plugin will not start without it).
4. Start the server – all configs and the PAPI expansion are auto‑generated.
5. Edit `config.yml` with your database credentials and server type.
6. Use `/bw setup` to build your first arena interactively.
7. Reload / restart. Done.

---

## Support & Purchasing

**BedWars Ultimate** is a premium plugin sold exclusively by the developer.

### How to buy
- **Discord:** `Nerotek01`
- **Bale (Iranian users):** `Nerotek`
- **Price:** **€25.00** (one‑time payment, lifetime license)

### What you get
- The full plugin JAR
- All 30+ integrated add‑ons
- Ranked system backend access and API token
- Free updates for the current major version
- **24/7 priority support** via Discord or Bale

### Support promise
When your server has a problem at peak time, you speak directly to the person who wrote the code. No waiting, no forums, no canned replies. Your uptime is our reputation.

---

## Roadmap

- **Private Games** – Invite‑only matches with host controls (kick, map select, team size)
- **Cosmetics** – Kill effects, victory dances, projectile trails, bed destruction effects, island toppers with rarity system
- **Continuous optimizations** – Further async offloading, profiling for 3000+ concurrent players
- **Expanded API** – More events, hooks, and full Javadoc coverage

---

**BedWars Ultimate** — The last BedWars plugin you will ever need to buy.
BedWars.joinQueue(player);
Map<String, Object> ranked = BedWars.getRankedStats(player);
api.getBedWarsCommand().addSubCommand(new MyCustomCommand());
