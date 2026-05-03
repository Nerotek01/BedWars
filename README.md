# BedWars · Ultimate Edition

> The most advanced, performance‑focused BedWars plugin for Minecraft 1.8.8 Spigot / Paper.  
> Built for large networks and demanding servers that refuse to compromise on quality.  
> **Tested and stable with over 2000 players online simultaneously.**

---

## Table of Contents

- [Why BedWars Ultimate?](#-why-bedwars-ultimate)
- [Feature Overview](#-feature-overview)
- [Ranked System (Full)](#-ranked-system-full)
- [Add‑ons](#-add‑ons)
- [Commands & Permissions](#-commands--permissions)
- [Configuration (100% Customizable)](#-configuration-100-customizable)
- [Database & Storage](#-database--storage)
- [Performance Optimizations](#-performance-optimizations)
- [PlaceholderAPI Integration](#-placeholderapi-integration)
- [BungeeCord & Auto‑Scale](#-bungeecord--auto-scale)
- [Public API](#-public-api)
- [Installation](#-installation)
- [Support & Purchasing](#-support--purchasing)
- [License](#-license)

---

## Why BedWars Ultimate?

Most BedWars plugins either lack features, perform poorly under load, or demand a dozen extra plugins to be usable.  
**BedWars Ultimate** was born from years of real‑world server administration. Every single line is written with **one goal: maximum player experience at zero TPS cost**.

### Key differentiators

| Feature | BedWars Ultimate | Other Popular Plugins |
|--------|-----------------|------------------------|
| **Gen Split, Deposit, Voidless etc.** | 30+ built‑in add‑ons – no extra JARs | Usually require separate plugins |
| **Ranked competitive system** | Fully integrated with Websocket, ELO, tournaments | Rarely native, often broken |
| **Database flexibility** | MongoDB + Redis (primary), SQLite fallback | Often only flat file or MySQL |
| **Performance** | Asynchronous DB, lazy chunk loading, generator rotation tuning | Many still run heavy sync operations |
| **Support** | 24/7 dedicated support via Discord | Community support or limited tickets |
| **Auto‑scale / BungeeCord** | Native, battle‑tested on networks with 1000+ concurrent players | Often buggy or missing |
| **Custom Quick Buy & Stats** | Player‑specific shop layouts, detailed stats GUI | Bare‑bones or absent |
| **Map reset** | SlimeWorldManager or internal adapter – instant reset | Slow file copy resets |
| **Customizability** | **100% configurable** – every mechanic, message, and add‑on | Limited or hard‑coded settings |
| **Scalability** | **Proven at 2000+ concurrent players** without TPS drop | Often untested at such scale |

When you choose BedWars Ultimate, you choose a plugin that doesn’t just work—it excels, even when your server is packed full.

---

## Feature Overview

### Core Gameplay
- Solo, Doubles, Triples, Quads (configurable per arena)
- Beds, generators, team upgrades, shop, and special items (fireballs, egg bridges, etc.)
- Full spectator mode with speed control, night vision, and auto‑teleport
- Rejoin capability – players can return to an ongoing game after a disconnect
- AFK auto‑kick
- Invisibility footsteps and custom invisibility handling
- TNT blast protection for end stone and glass (configurable multipliers)
- World border enforcement
- Void‑safe fallback (Voidless add‑on)
- Water height limiter, adventure mode, anti‑drop, item deposit (team chest with hologram)

### Server Modes
- **Multi‑Arena** – many arenas on one server
- **BungeeCord** – one arena per server, connected via a dedicated socket
- **Auto‑Scale** – automatically spin up new game servers as demand rises (requires orchestration)
- **Shared** – custom team‑based mode for special events

### Additional Systems
- Party support (Parties plugin or internal, fully configurable)
- Chat formatting and `/shout` command
- Custom scoreboard (sidebar) with live game updates
- Token‑based economy (no Vault required) – earn tokens by winning, breaking beds, etc.
- Level & XP system with configurable requirements
- Fully configurable shop, generators, and upgrade paths

---

## Ranked System (Full)

The ranked mode transforms BedWars into a competitive, elo‑based season‑driven experience.

- **WebSocket API** – connects to a central ranked server to fetch queues, elo, and match results.
- **Automated matchmaking** – players join a ranked queue; the system creates games when enough players are ready.
- **ELO rating** – win/lose against equally‑skilled players; seasons reset periodically (optional).
- **Tournament NPCs** – seasonal NPCs in the lobby display rules, top players, and allow queue entry.
- **In‑game restrictions** – separate shop and upgrade restrictions for ranked (e.g., disabling certain items).
- **Player Profile Management** – every player has a ranked profile with detailed statistics (wins, losses, kills, elo history).
- **Leaderboard** – holographic leaderboard updated in real‑time via Redis.
- **PlaceholderAPI expansion** – use `%bw_ranked_elo%`, `%bw_ranked_wins%`, etc. anywhere.
- **Admin utilities** – through API utils (`APIUtils`) and internal managers, you can inspect, modify, and debug ranked data.

The ranked system requires a valid API token and access to a Ranked‑service backend. Contact us for setup assistance.

---

## Add‑ons

Every add‑on is a self‑contained module that can be enabled/disabled inside `addons.yml`.  
No extra plugins, no messy dependencies. The plugin is **100% modular** – you enable only what you need.

| Add‑on | Description |
|--------|-------------|
| **Ranked** | Full competitive queue, ELO, WebSocket, tournaments |
| **Play Again** | Quick re‑queue item after game ends |
| **Team Selector** | GUI to choose team before start |
| **Spectator Options** | Speed, night vision, auto‑teleport |
| **Compass** | Enemy/team tracker compass with menu |
| **Quick Buy** | Persistent, per‑player quick‑buy slots |
| **Arena Start Message** | Title/subtitle at game start |
| **Reward Summary** | Detailed post‑game rewards breakdown |
| **Voidless** | Teleport to base instead of dying in void |
| **BossBar** | Custom boss bar with game info |
| **Hotbar Manager** | Auto‑arrange tools and blocks |
| **Stats Menu** | Interactive stats GUI (kills, wins, beds) |
| **Map Selector** | Voting system for the next map |
| **Leaderboard** | Holographic top players in lobby |
| **Water Height Limit** | Prevents water placement above Y limit |
| **Adventure Mode** | Forces adventure mode in arenas |
| **Anti Drop** | Disables item dropping (except whitelisted) |
| **Gen Split** | Evenly splits generator loot among nearby teammates |
| **Height Limit Notifier** | Warns near build limit |
| **Invisibility Footsteps** | Particle footsteps for invisible players |
| **Deposit** | Deposit resources into a team chest (hologram) |
| **Level Bar** | XP bar shows player level progress |
| **Sponge** | Sponge water removal mechanics |
| **Token Economy** | Internal token system (no Vault) |

… and more. If an add‑on is disabled, its listeners and tasks are completely unloaded—zero performance impact.

---

## Commands & Permissions

Main command: `/bw` (alias `/bedwars`)

### Player Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw join <arena>` | Join a specific arena | `bw.player` |
| `/bw leave` | Leave current game | `bw.player` |
| `/bw rejoin` | Rejoin last game | `bw.player` |
| `/bw shout` | Global game chat | `bw.player` |
| `/bw spectate <player>` | Spectate another player | `bw.spectate` |
| `/bw map` | Vote for next map | `bw.player` |
| `/bw stats [player]` | View statistics | `bw.player` |
| `/bw compass` | Open tracker compass menu | `bw.player` |
| `/map` | Shortcut to map voting | `bw.player` |
| `/leave` | Leave game (if not overridden) | `bw.player` |

### Admin Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw setup` | Interactive arena creation | `bw.admin` |
| `/bw lobby` | Set lobby spawn point | `bw.admin` |
| `/bw process` | Debug / management tasks | `bw.admin` |
| `/statistics` | Admin stats view | `bw.admin` |

All permissions are autogenerated and can be managed via any permissions plugin.

---

## Configuration (100% Customizable)

All configuration files are stored in `plugins/BedWars/`.  
**Every aspect of the plugin can be changed** – messages, game mechanics, economy, shop, generators, add‑ons, database, and much more. No hard‑coded values, no hidden behavior.

| File | Role |
|------|------|
| `config.yml` | Server type, database, lobby, general settings |
| `generators.yml` | Generator timing, resources, tiers |
| `shop.yml` | Shop categories, prices, quick‑buy defaults |
| `addons.yml` | Toggle individual add‑ons on/off |
| `messages_en.yml` (language folder) | All plugin messages (multi‑language) |
| `levels.yml` | XP required per level |
| `money.yml` | Token rewards per action |
| `ranked.yml` | Ranked API keys and options |
| `Arenas/*.yml` | One file per arena, fully generated by `/bw setup` |

Changes to most configuration files can be applied with a simple reload (the plugin internally handles re‑reading), though a full restart is recommended for certain changes.

---

## Database & Storage

The plugin uses a multi‑layered storage strategy:

- **MongoDB** – primary database for player stats, quick‑buy slots, levels, and ranked profiles.  
  Asynchronous writes and reads keep the main thread free.
- **Redis** – cross‑server stats synchronization and real‑time leaderboard updates.  
  Optional but highly recommended for networks.
- **SQLite** – fallback database. Activated automatically when MongoDB is disabled or unavailable.  
  Not suitable for production networks.

The `DatabaseProvider` ensures a unified interface; no matter which engine is used, the code remains the same.

---

## Performance Optimizations

We treat performance as a feature, not an afterthought.  
**BedWars Ultimate has been stress‑tested with over 2000 concurrent players across a network** and maintained a stable 20 TPS.

- **Generator rotation** runs on a dedicated scheduler at a lower frequency (configurable, default 120 ticks) instead of every tick.
- **All database operations** (MongoDB, Redis) are executed asynchronously.
- **Chunk loading** is done lazily when a player joins an arena, not pre‑loaded all at once.
- **World reset** leverages SlimeWorldManager when available—worlds are reloaded from templates almost instantly without heavy I/O.
- **Entity cleanup** removes all monsters from lobby worlds automatically.
- **Event listeners** are registered only for enabled add‑ons, and properly unregistered on shutdown.
- **The scoreboard** is updated only when necessary, not every tick.
- **TNT and explosion calculations** are customised to be both balanced and light on the CPU.

The result: even with 2000+ players across multiple arenas, the server stays rock‑solid.

---

## PlaceholderAPI Integration

The plugin automatically registers a PlaceholderAPI expansion, providing a wide range of placeholders:

| Placeholder | Example Output |
|-------------|----------------|
| `%bw_level%` | `12` |
| `%bw_kills%` | `324` |
| `%bw_deaths%` | `45` |
| `%bw_wins%` | `67` |
| `%bw_beds_broken%` | `103` |
| `%bw_tokens%` | `2,450` |
| `%bw_current_arena%` | `solo_01` |
| `%bw_team_color%` | `RED` |
| `%bw_game_state%` | `PLAYING` |
| `%bw_ranked_elo%` | `1342` |
| `%bw_ranked_wins%` | `42` |

Use them in any PlaceholderAPI‑compatible plugin (holograms, scoreboards, etc.).

---

## BungeeCord & Auto‑Scale

Designed for networks that need to grow dynamically.

- **BungeeCord mode** – each server hosts exactly one arena. Game servers register with the lobby.
- **Auto‑scale** – the lobby server monitors player counts and can signal your infrastructure to start new game servers.
- **WebSocket communication** ensures that game results and player data are synced across the whole network.

The built‑in `ArenaSocket` and `SendTask` manage all the heavy lifting. Only a minimal orchestration script is needed.

---

## Public API

Plug into BedWars Ultimate from your own plugins:

```java
BedWars api = BedWars.getAPI();

// Get an arena
IArena arena = api.getArenaByName("myarena");

// Join the ranked queue
BedWars.joinQueue(player);

// Get player ranked stats
Map<String, Object> ranked = BedWars.getRankedStats(player);

// Register your own subcommand
api.getBedWarsCommand().addSubCommand(new MyCustomCommand());
