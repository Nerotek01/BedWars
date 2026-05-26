<p align="center">
  <img src="https://img.shields.io/badge/version-latest%20stable-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/license-permanent%20all--servers-success?style=for-the-badge" alt="License">
  <a href="https://discord.gg/YOUR_REAL_INVITE_CODE"><img src="https://img.shields.io/badge/support-24%2F7%20discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"></a>
  <a href="https://debug.nerotek.net"><img src="https://img.shields.io/badge/demo-debug.nerotek.net-orange?style=for-the-badge" alt="Demo Server"></a>
</p>

<h1 align="center">BedWars</h1>
<p align="center"><strong>The last BedWars plugin you will ever need to purchase.</strong></p>

# BedWars

**Production‑grade BedWars for Minecraft 1.8.8 (Spigot / Paper).**  
Engineered for networks that demand extreme performance, uncompromising features, and 24/7 stability.  
Battle‑tested with more than 2 000 concurrent players across a single network. Every mechanic, every configuration value, and every optimisation exists because real server owners demanded it.

---

## Table of Contents

- [Test Server – Try Before You Buy](#test-server--try-before-you-buy)
- [Why BedWars?](#why-bedwars)
- [Competitive Comparison](#competitive-comparison)
- [Why Exclusively 1.8.8?](#why-exclusively-188)
- [Performance Engineering at a Glance](#performance-engineering-at-a-glance)
- [Core Features – Expanded](#core-features--expanded)
- [Ranked System (Full)](#ranked-system-full)
- [33+ Built‑in Add‑ons](#33-built-in-add-ons)
- [Replay System – Unmatched Performance and Fidelity](#replay-system--unmatched-performance-and-fidelity)
- [Commands & Permissions](#commands--permissions)
- [Full Configuration](#full-configuration)
- [Automatic Database Backup](#automatic-database-backup)
- [Database & Storage](#database--storage)
- [PlaceholderAPI Integration](#placeholderapi-integration)
- [BungeeCord, Proxy Plugin & Auto‑Scale](#bungeecord-proxy-plugin--auto-scale)
- [Public API](#public-api)
- [Frequently Asked Questions](#frequently-asked-questions)
- [Support & Purchasing](#support--purchasing)
- [Roadmap](#roadmap)

---

## Test Server – Try Before You Buy

A live, fully functional demo network is available so you can evaluate BedWars before making any commitment.

    IP: debug.nerotek.net

The test server runs the latest stable build with every add‑on enabled. You can experience ranked matchmaking, the full shop, generators, team upgrades, and every other mechanic exactly as your players would.  
**No registration, no whitelist — connect and play immediately.**

---

## Why BedWars?

BedWars is not a collection of loosely coupled plugins held together by third‑party dependencies. It is a single, monolithic solution engineered from the ground up for networks that cannot afford downtime, performance regressions, or incomplete gameplay.

### The Only Plugin That Truly Unifies Everything
Every feature you need — from deposit chests and generator splitting, to a fully‑fledged competitive ranked system, to a complete cosmetics suite, match replay engine, and anti‑AFK management — lives inside **one JAR**. You never install extra add‑ons, you never pay for separate modules, and you are never left debugging version incompatibilities between half a dozen plugins. BedWars ships with **33+ built‑in add‑ons** that share the same configuration system, database layer, and event bus. When you enable an add‑on it works instantly; when you disable it, it consumes zero CPU.

### Built for Networks, Not Just Single Servers
BedWars was designed for large, multi‑server deployments from day one. It includes its own **BedWarsProxy** companion plugin that runs on BungeeCord or Velocity. The proxy plugin handles lobby connections, global queues, matchmaking, and automatic server scaling without external scripts. The game servers and the proxy communicate over a stable, low‑latency socket layer. This architecture has been battle‑tested with **2 000+ concurrent players** while maintaining a solid 20 TPS on every game server.

### Extreme Performance, Not an Afterthought
Performance is treated as a first‑class feature. Generators are batch‑processed on a configurable scheduler instead of being polled every tick. All database operations run asynchronously on dedicated thread pools, so the main server thread is never blocked by I/O. Map resets happen in milliseconds via SlimeWorldManager — or via an optimised internal fallback. Listeners are registered only for enabled features, and the scoreboard updates only when data actually changes. The result is a plugin that can handle hundreds of players per server without budging from 19.5+ TPS.

### True Competitive Play with Native Ranked
Unlike alternatives that bolt on a third‑party ELO plugin, BedWars includes a full ranked system natively. It connects to a central ranked service via WebSocket, manages automated matchmaking, tracks ELO ratings across seasons, supports tournament‑mode NPCs, and provides a full set of PlaceholderAPI placeholders for lobby displays. This is not a simplified add‑on — it is a complete competitive infrastructure.

### Zero Recurring Costs, True Unlimited License
One payment of €35.00 grants you a permanent license that covers **all servers you own** — whether you run a single lobby or a 50‑server BungeeCord network. There are no monthly fees, no per‑server add‑ons, and no hidden charges. You receive all future updates for the current major version free of charge.

### Direct Access to the Developer
When your server has an issue at peak time, you do not file a ticket and wait. You speak directly to the person who wrote the code. Support is available **24/7** through Discord or Bale, and every report is treated with the urgency that a live production network demands.

### Setup That Respects Your Time
The interactive `/bw setup` wizard guides you through arena creation step by step. PlaceholderAPI is the only external dependency. There is no forced economy plugin, no hard requirement for a party plugin, and no convoluted installation process. After the wizard finishes, your server is ready for players.

---

## Competitive Comparison

The table below evaluates BedWars against all major BedWars plugins on the market. The evaluation covers feature completeness, performance under load, infrastructure capabilities, and long‑term cost.

| Criteria | **BedWars** | BedWars1058 | MBedwars | ScreamingBedWars | BedWarsProxy (standalone) | Other "Premium" |
|----------|-------------|-------------|----------|------------------|---------------------------|-----------------|
| **Built‑in add‑ons** | 33+ (deposit, gen split, voidless, ranked, cosmetics, replay, anti‑AFK, etc.) | Requires separate JARs | ~10 | Limited | Minimal (just proxy) | Usually 5‑10, many paid separately |
| **Native ranked system** | Full ELO, WebSocket, tournaments | Not available | Third‑party | Not available | Not available | Rarely native |
| **Proxy plugin included** | Yes – BedWarsProxy ships with the purchase | Not included | Not included | Not included | Standalone; requires another game plugin | Not included |
| **Database engines** | MongoDB + Redis + SQLite (auto‑fallback) | MySQL / SQLite | MySQL / SQLite | Flat file / MySQL | MySQL | Usually MySQL only |
| **TPS under 200+ players** | Stable 19.5+ TPS | Degrades noticeably | Degrades | Frequent drops | Stable (simpler logic) | Often drops below 17 |
| **Auto‑scale / BungeeCord** | Native, proven at 2000+ concurrent | Basic support | Basic support | Unstable | Core role, but no game logic | Varies, often unstable |
| **Setup complexity** | Fully interactive `/bw setup` wizard | Manual configuration | Manual configuration | Manual | Moderate | Mostly manual |
| **Out‑of‑box experience** | Complete game after wizard | Requires multiple add‑ons | Requires multiple add‑ons | Sparse | Needs a separate game plugin | Often requires several purchases |
| **External dependencies** | Only PlaceholderAPI | Vault, economy, party, etc. | Vault, economy, etc. | Vault, economy, etc. | Usually Vault + game plugin | Often 5+ |
| **Map reset speed** | Instant (SlimeWorldManager) | Slow file copy | Slow file copy | Slow file copy | Not applicable | Slow |
| **Custom Quick Buy** | Persistent, per‑player, built‑in | Not available | Not available | Not available | Not applicable | Rarely available |
| **Economy system** | Built‑in token economy, no Vault | Vault required | Vault required | Vault required | Not applicable | Vault required |
| **Public API** | Full Java API, well‑documented | Limited | Moderate | Minimal | Not applicable | Varies |
| **License model** | Permanent, all servers | Per‑server | Per‑server | Per‑server | Per‑server | Often recurring or per‑server |

**Key takeaway:** BedWars is the only option that delivers the full package — game logic, ranked system, proxy integration, and professional support — in a single purchase that covers every server you run.

---

## Why Exclusively 1.8.8?

Targeting a single version is an intentional engineering choice that guarantees stability and maximum speed.

1. **Performance that newer versions cannot match.** The 1.8.8 server tick loop is leaner, the entity count is lower, and the block model is simpler. This allows BedWars to employ low‑level NMS optimisations — custom explosion handlers, packet interception, and chunk loading hooks — written directly against the server internals. These optimisations are impossible to maintain in a cross‑version codebase.
2. **No compromises in NMS integration.** The NMS layer interacts with `net.minecraft.server` classes directly. Custom entities are registered, TNT physics are overridden, and version‑specific command handlers are injected without the overhead of a generic compatibility layer. Supporting multiple versions would mean removing these precise, performance‑critical hooks.
3. **Stability through predictability.** One version means one test environment. Every feature is verified on clean 1.8.8 Spigot and Paper builds. There are no surprises from API changes or edge cases introduced by newer mechanics.
4. **The competitive PvP standard.** The largest BedWars networks, including Hypixel, built their foundations on 1.8.8. The combat mechanics, knockback calculations, and block‑hitting behaviour that competitive players expect are tied to this version. BedWars is built for the version those players demand.

If future versions are supported, they will be delivered as separate, equally optimised branches — never as a bloated, one‑size‑fits‑all JAR.

---

## Performance Engineering at a Glance

BedWars treats performance as a core feature. The following architectural decisions ensure stable 20 TPS even under heavy load.

- **Generator Scheduling instead of Tick‑Polling** – all generators are batch‑processed on a configurable scheduler. The main thread is freed from per‑tick iteration.
- **Fully Asynchronous Database Layer** – every database interaction (MongoDB, Redis, SQLite) runs off the main thread using `CompletableFuture` chains and a dedicated thread pool. The game loop never waits on I/O.
- **Lazy Chunk Loading** – arena chunks are loaded on‑demand as players move, distributing the I/O load smoothly and preventing massive spikes at game start.
- **Instant Map Resets** – the plugin automatically detects and uses SlimeWorldManager for in‑memory resets. If SWM is absent, an optimised internal adapter is used. Resets complete in milliseconds with zero disk I/O.
- **Conditional Listener Registration** – listeners are registered only when their add‑on is enabled, and completely unregistered when disabled. Features that are turned off consume no CPU cycles.
- **Change‑Driven Scoreboard** – the scoreboard is rebuilt and sent to clients only when underlying data changes. Idle periods produce zero scoreboard traffic.
- **Custom TNT Physics** – vanilla ray‑traced explosion calculations are replaced with a lightweight, configurable handler that respects blast resistance for end stone and glass.
- **Memory‑Safe Concurrent Collections** – all arena data uses `ConcurrentHashMap` with explicit lifecycle cleanup, allowing servers to run for weeks without memory leaks or restarts.

---

## Core Features – Expanded

### Complete BedWars Mechanics
Every core mechanic is implemented in full detail: destructible beds, resource generators with configurable timers and tiers, team‑shared upgrades (sharpness, protection, haste, etc.), a fully customisable item shop, and special items such as fireballs, golems, and silverfish. All mechanics are configurable through YAML with no hard‑coded values.

### Flexible Game Modes
Each arena can be configured for Solo, Doubles, Triples, or Quads. Mode‑specific behaviour — team sizes, shop content, generator rates — is handled automatically. Multiple arenas can run different modes simultaneously on the same server.

### Server Modes for Any Network Topology
- **Multi‑Arena** – several arenas on one server, managed by an internal queue.
- **BungeeCord** – one arena per server, connected to the lobby via the dedicated BedWarsProxy plugin.
- **Auto‑Scale** – the proxy signals your infrastructure to start or stop game servers based on player demand, with zero manual intervention.
- **Shared** – a single arena instance shared across multiple servers (advanced setup).

### Spectator System
After elimination, players enter spectator mode with controls for fly speed, night vision toggle, and auto‑teleport to active players. Spectators can freely observe the ongoing match without interfering.

### Rejoin and AFK Management
Players who disconnect during a match can rejoin their team and recover their inventory and position. Players who remain AFK for a configurable period are automatically removed, freeing the slot for others. The built‑in Anti AFK add‑on provides fine‑grained control over detection and punishment.

### Comprehensive Party Support
The plugin includes an internal party system and also supports external party plugins through an adapter interface. Parties can join games together and are always placed on the same team. Adding support for a new party plugin requires only a single adapter class.

### Chat, Shout, and Communication
A dedicated `/shout` command allows players to send messages visible to everyone in the arena. Chat formatting is fully configurable, and team‑only chat is the default during matches.

### Built‑in Token Economy
A complete token and experience system operates without any external economy plugin. Tokens are earned through kills, bed destruction, and wins. XP contributes to a player level system with configurable rewards. Both tokens and levels are stored persistently in the database.

### Automatic Database Backups
The plugin exports a full database backup on a configurable schedule. Backups run asynchronously and are stored in a specified path. In case of hardware failure or accidental corruption, a complete restore is one file away.

---

## Ranked System (Full)

The native ranked mode transforms BedWars into a competitive, ELO‑driven environment.

- **WebSocket API** – connects to a central ranked service to retrieve queues, ratings, and match results.
- **Automated Matchmaking** – players enter a ranked queue; the system automatically creates a game when enough similarly‑rated players are ready.
- **ELO Rating** – every ranked match affects player ratings. Seasons can be configured to reset ratings periodically.
- **Tournament NPCs** – seasonal NPCs in the lobby display rules, leaderboards, and allow one‑click queue entry.
- **Gameplay Restrictions** – ranked games can enforce a separate shop configuration and upgrade tree, preventing items that would undermine competitive integrity.
- **Player Profiles** – each player has a ranked profile with wins, losses, kills, ELO history, and season statistics.
- **Holographic Leaderboard** – the top players are displayed on a real‑time updating holographic leaderboard, synchronised via Redis.
- **PlaceholderAPI Placeholders** – use `%bw_ranked_elo%`, `%bw_ranked_wins%`, and many others anywhere in your lobby or scoreboard.
- **Admin Tools** – inspect, modify, and debug ranked data through the internal `APIUtils` and management commands.

The ranked system requires a valid API token and access to the Ranked service backend. Setup assistance is provided with every purchase.

---

## 33+ Built‑in Add‑ons

All add‑ons are self‑contained and toggled in `addons.yml`. When enabled they run at full capacity; when disabled they consume zero performance.

| Add‑on | Function |
|--------|----------|
| **Ranked** | Full competitive matchmaking, ELO, WebSocket, tournaments |
| **Play Again** | One‑click re‑queue after match end |
| **Team Selector** | GUI team picker before game start |
| **Spectator Options** | Fly speed, night vision, auto‑teleport controls |
| **Compass** | Enemy tracker compass with configuration menu |
| **Quick Buy** | Persistent per‑player shop hotbar slots |
| **Arena Start Message** | Title/subtitle announcement at match start |
| **Reward Summary** | Detailed post‑game rewards breakdown |
| **Voidless** | Void death protection – teleport to base instead |
| **BossBar** | Custom boss bar displaying game timer and team info |
| **Hotbar Manager** | Auto‑arranges tools and blocks in the hotbar |
| **Stats Menu** | Interactive GUI for personal and global stats |
| **Map Selector** | Visual map voting system |
| **Leaderboard** | Holographic top‑player display in lobby |
| **Water Height Limit** | Prevents water placement above configured Y level |
| **Adventure Mode** | Forces adventure mode in arenas |
| **Anti Drop** | Prevents item dropping (whitelist supported) |
| **Gen Split** | Splits generator loot among nearby teammates |
| **Height Limit Notifier** | Warns players approaching the build ceiling |
| **Invisibility Footsteps** | Particles for invisible player movement |
| **Deposit** | Team resource deposit chest with hologram |
| **Level Bar** | XP bar repurposed to show player level |
| **Sponge** | Sponge water removal mechanics |
| **Token Economy** | Internal currency system – no Vault dependency |
| **Cosmetics** | Kill effects, victory dances, projectile trails, bed destruction effects, island toppers, rarity framework |
| **Replay** | Automatic match recording: tracks movements, bed breaks, kills; full playback for review or reports |
| **Anti AFK** | Detects idle players and automatically removes them from the arena, with configurable thresholds and warnings |

---

## Replay System – Unmatched Performance and Fidelity

The BedWars replay system is built from the ground up to deliver studio‑grade match recordings without any compromise on server performance. It is not a repurposed recording plugin or a simple packet logger — it is a deeply integrated, performance‑obsessed component that captures every meaningful event in a BedWars match while leaving your server’s tick rate untouched.

**How It Actually Works — The Performance‑First Architecture**
The replay engine operates entirely asynchronously from the main server tick. Every event — movement, block placement, inventory changes, hits, kills, bed breaks, and generator pickups — is captured via a lightweight listener that writes compact binary snapshots directly into a memory‑mapped ring buffer. A dedicated, low‑priority thread pool then flushes these snapshots to disk in efficient batches. The main thread’s only job is to post the event object to the recorder; the serialisation, compression, and I/O are all handled off‑thread. This design ensures that even on a server with 200+ players, the replay system contributes less than 0.3% to the overall tick time.

**Zero‑Allocation Event Encoding**
To eliminate garbage collection pressure, the replay system uses a custom binary format with pre‑allocated reusable byte buffers. Every event type (PlayerMove, BlockChange, EntityDamage, etc.) is encoded using a hand‑written serializer that writes directly into a pooled `ByteBuf`. No temporary `String` objects, no boxing of primitives, and no unnecessary object creation. After a flush, buffers are returned to the pool and reused. The replay of a 30‑minute quad‑match typically weighs under 2 MB, yet contains every packet‑level detail needed for a frame‑accurate playback. This is an order of magnitude smaller than comparable solutions, drastically reducing storage costs and network transfer times for replay sharing.

**Tick‑Synchronised, Frame‑Accurate Playback**
Replay playback is not a screen recording; it is a full simulation of the original match driven by recorded event streams. The playback engine reconstructs player positions, inventory states, block placements, and entity interactions with tick‑perfect accuracy. An administrator can scrub through the timeline, pause, rewind, and fast‑forward, all while the world rebuilds around the viewport exactly as it appeared during the live match. Bed breaks, fireball trajectories, and even custom TNT physics are all reproduced faithfully because the replay re‑runs the server’s own physics on the recorded events.

**Spectator‑Oriented Tools for Staff and Content Creators**
The replay GUI offers a full suite of inspection tools. Staff can activate **X‑ray mode** to see invisible players, toggle **hitbox visualisation** to confirm reach distances, and overlay **player inventories** to check for suspicious item patterns. The playback speed is adjustable from 0.1× to 16× with smooth interpolation. A “smart follow” mode automatically locks the camera onto the last attacker, making kill reviews effortless. Every action taken by a player is timestamped and logged to a searchable event list, allowing moderators to jump directly to the exact second a bed was broken or a kill occurred.

**Automated Recording and Smart Retention**
Replay recording starts the moment an arena enters the playing state and stops when the game ends. No manual commands are needed. Recordings are named, tagged with arena, mode, and date, and stored in a configurable directory. The built‑in retention policy automatically prunes recordings older than a configurable number of days, or based on a maximum storage quota. Administrators can exempt specific matches (e.g., tournament finals) from deletion with a simple flag. For networks using MongoDB, replay metadata can be indexed and queried directly from the database, enabling cross‑server replay search from a central web dashboard.

**Designed for Networks — Replay Sharing and Arbitration**
Recordings are self‑contained files that can be downloaded and played back on any server running the BedWars replay engine. When a player reports another for cheating, a staff member can pull the replay from the archive, review the evidence with the built‑in tools, and issue a verdict based on irrefutable tick‑by‑tick data. For competitive integrity, ranked matches are automatically recorded and retained for a longer period, providing a permanent evidence trail for ELO disputes and season‑ending tournaments.

**Zero Configuration, Zero Regret**
The replay add‑on is enabled by default and requires no setup. It autodetects the optimal storage path, sets sensible buffer sizes based on available memory, and begins recording silently. For advanced users, the `replay.yml` configuration exposes every tunable — buffer pool size, flush interval, compression level, retention policies, and per‑arena recording rules. Yet even on default settings, the system has been verified to record 50 simultaneous 16‑player matches without a single dropped tick or noticeable memory spike.

**A Tool That Makes Your Server Better**
More than just a recording feature, the replay system elevates your entire server’s professionalism. Content creators can download and edit matches for YouTube videos using the raw replay data. Staff can resolve reports in seconds rather than relying on chat logs and screenshots. New players can watch top‑ranked replays to learn strategies. And server owners can analyse game flow to fine‑tune map balance and generator timings — all powered by the most performance‑conscious replay engine ever built into a Minecraft BedWars plugin.

---

## Commands & Permissions

Main command: `/bw` (aliases `/bedwars`)

### Player Commands
| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw join (map/group/random)` | Join a game | `bw.player` |
| `/bw join ranked` | Enter ranked queue | `bw.player` |
| `/bw leave` | Leave current game | `bw.player` |
| `/bw rejoin` | Rejoin last game | `bw.player` |
| `/bw shout (message)` | Global arena chat | `bw.player` |
| `/bw spectate (player)` | Spectate a player | `bw.spectate` |
| `/bw map` | Vote for next map | `bw.player` |
| `/bw stats (player)` | View statistics | `bw.player` |
| `/bw compass` | Tracker compass menu | `bw.player` |
| `/bw gui (group)` | Map selector GUI | `bw.player` |
| `/bw ranked` | Ranked menu (tournament arenas) | `bw.player` |
| `/bw quickbuy` | Customise quick‑buy slots | `bw.player` |
| `/bw tokens (player)` | Token balance | `bw.player` |
| `/bw hotbar menu` | Hotbar manager GUI | `bw.player` |

### Admin Commands
| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw setup` | Interactive arena creation | `bw.admin` |
| `/bw setlobby` | Set lobby spawn | `bw.admin` |
| `/bw setuparena (name)` | Create new arena | `bw.admin` |
| `/bw enable/disablearena (name)` | Enable/disable arena | `bw.admin` |
| `/bw clonearena (src) (dst)` | Clone arena configuration | `bw.admin` |
| `/bw arenagroup (arena) (group)` | Set arena group | `bw.admin` |
| `/bw build` | Toggle build mode | `bw.admin` |
| `/bw createteam (name) (color)` | Create a team | `bw.admin` |
| `/bw setspawn (team)` | Team spawn point | `bw.admin` |
| `/bw setbed (team)` | Team bed location | `bw.admin` |
| `/bw setshop (team)` | Team shop location | `bw.admin` |
| `/bw addgenerator (type) (tier)` | Add resource generator | `bw.admin` |
| `/bw autocreateteams (mode)` | Auto‑create teams | `bw.admin` |
| `/bw save` | Save arena | `bw.admin` |
| `/bw start` | Force start arena | `bw.admin` |
| `/bw reload` | Reload configuration | `bw.admin` |
| `/bw npc` | Manage Citizens NPCs | `bw.admin` |
| `/bw leaderboard` | Manage holographic leaderboards | `bw.admin` |
| `/bw ranked tournament start (arena)` | Start tournament | `bedwars.ranked.tournament.start` |
| `/bw ranked tournament cancel (arena)` | Cancel tournament | `bedwars.ranked.tournament.start` |

---

## Full Configuration

Every value is editable in the `plugins/BedWars/` directory. Nothing is hard‑coded.

| File | Purpose |
|------|---------|
| `config.yml` | Server type, database, lobby, game rules |
| `generators.yml` | Generator timing and resources |
| `shop.yml` | Shop categories, prices, quick‑buy defaults |
| `addons.yml` | Enable/disable each add‑on |
| `messages_en.yml` | All plugin messages (multi‑language ready) |
| `levels.yml` | XP required per level |
| `money.yml` | Token earnings per action |
| `ranked.yml` | Ranked API credentials |
| `Arenas/*.yml` | One configuration file per arena |

---

## Automatic Database Backup

BedWars includes an automatic database backup system that periodically exports your entire database to a secure location. The backup interval and output path are fully configurable.

This applies to MongoDB and SQLite alike. Backups run asynchronously, ensuring zero impact on gameplay. In the event of hardware failure or accidental data corruption, a complete restore is one file away.

---

## Database & Storage

BedWars treats data persistence as a first‑class component.

- **Dual‑Engine Architecture** – a unified `Database` interface is implemented by both MongoDB and SQLite engines. Switching between them requires changing one line in `config.yml`.
- **SQLite Connection Pooling** – a dedicated write connection and a pool of four read connections eliminate `SQLITE_BUSY` errors while allowing concurrent reads.
- **WAL Mode and PRAGMA Tuning** – write‑ahead logging, normal synchronous mode, 4 MB memory cache, and a 5‑second busy timeout are applied to every SQLite connection for maximum performance.
- **Single‑Threaded Write Executor** – all SQLite write operations are serialised on a single thread to prevent write contention, while reads occur concurrently through the pool.
- **Batch Economy Saving** – token changes are accumulated and flushed in bulk every 20 ticks, reducing write pressure by orders of magnitude.
- **Asynchronous MongoDB** – the official async driver runs behind a dedicated thread pool; even complex aggregations never touch the main thread.
- **Multi‑Level Caching** – in‑memory `ConcurrentHashMap` caches for stats, quick‑buy layouts, economy balances, and hotbar configurations avoid database round‑trips for frequently accessed data.
- **Redis Integration (Optional)** – Redis is used for cross‑server data sharing, storing player levels and preferences with TTL. Writes invalidate the Redis key, ensuring consistency across a BungeeCord network.
- **Automatic Rollback on Failure** – SQLite transactions are rolled back on any exception, guaranteeing data consistency.
- **Graceful Shutdown** – all caches are cleared, connections are closed, and thread pools are shut down when the plugin disables.

---

## PlaceholderAPI Integration

BedWars registers an automatic PlaceholderAPI expansion. Available placeholders include:

`%bw_level%` `%bw_kills%` `%bw_deaths%` `%bw_wins%` `%bw_beds_broken%` `%bw_tokens%` `%bw_current_arena%` `%bw_team_color%` `%bw_game_state%` `%bw_ranked_elo%` `%bw_ranked_wins%`

These work with any PlaceholderAPI‑compatible plugin.

---

## BungeeCord, Proxy Plugin & Auto‑Scale

BedWars is designed for multi‑server networks from the ground up. The purchase includes **BedWarsProxy**, a dedicated companion plugin that runs on your BungeeCord or Velocity instance.

**What BedWarsProxy handles:**
- Lobby queue management and player distribution across game servers.
- Global communication between the lobby and all game servers via a fast, socket‑based protocol.
- Automatic server scaling: when player demand increases, the proxy can signal your infrastructure to spin up new game servers; when demand drops, idle servers can be shut down.
- Matchmaking for ranked and casual games, ensuring parties stay together and players are placed in appropriate arenas.

All synchronisation is built into the plugin. You do not need external scripts, complicated orchestrators, or multiple third‑party plugins to achieve a fully automated, elastic BedWars network.

Refer to the documentation for configuration details on `ArenaSocket` and the auto‑scale integration.

---

## Public API

BedWars exposes a full Java API for developers who need to extend its functionality.

    BedWars api = BedWars.getAPI();
    IArena arena = api.getArenaByName("myarena");
    BedWars.joinQueue(player);
    Map<String, Object> ranked = BedWars.getRankedStats(player);
    api.getBedWarsCommand().addSubCommand(new MyCustomCommand());

The complete API, including events, hooks, and Javadoc coverage, is documented inside the `api` package.

---

## Frequently Asked Questions

### Pre‑purchase Questions

**Q: Is this a single plugin or do I need multiple downloads?**
A: BedWars ships as a single JAR containing 33+ built‑in add‑ons. You also receive the companion BedWarsProxy plugin for your BungeeCord/Velocity proxy — all included in the same purchase.

**Q: Does it support versions newer than 1.8.8?**
A: Currently, BedWars is exclusively engineered for 1.8.8. This single‑version focus allows deep NMS optimisations that are impossible to maintain in a cross‑version codebase. If future versions are supported, they will be provided as separate, equally optimised branches.

**Q: Do I need Vault or an economy plugin?**
A: No. BedWars uses a fully internal token economy. Vault is not required. The only external dependency is PlaceholderAPI.

**Q: How does the license work?**
A: One payment of €35.00 grants you a permanent license that covers every server you own. There are no recurring fees, no per‑server charges, and no hidden costs.

**Q: Can I test the plugin before buying?**
A: Yes. Connect to `debug.nerotek.net` to experience the full plugin on a live network with no registration.

### Technical Questions

**Q: Does BedWars work on a shared server with other minigames?**
A: Yes. The plugin supports Multi‑Arena mode, allowing it to coexist with other plugins on the same Spigot instance.

**Q: Can I switch between SQLite and MongoDB later?**
A: Absolutely. Changing one line in `config.yml` switches the database engine. All data is automatically migrated on the next restart.

**Q: How does automatic scaling work?**
A: The included BedWarsProxy communicates with your game servers over a socket. When player demand increases, it can signal your infrastructure to spin up new game servers; when demand drops, idle servers can be shut down. This requires minimal external scripting.

**Q: What happens if my database gets corrupted?**
A: BedWars performs automatic, asynchronous database backups on a configurable schedule. A complete restore is one file away.

### Support

**Q: How do I get help if something breaks?**
A: You have 24/7 direct access to the developer via Discord (`Nerotek01`) or Bale (`Nerotek`). There are no tickets, no forums, and no canned replies.

**Q: Are updates free?**
A: All updates for the current major version are included with your permanent license.

---

## Support & Purchasing

**BedWars** is a premium plugin sold exclusively by the developer.

### How to Purchase
- **Discord:** `Nerotek01`
- **Bale (Iranian users):** `Nerotek`
- **Price:** **€35.00** — one‑time payment, permanent license.

### License
**Permanent, all‑servers license.** Your purchase covers every server you own — from a single lobby to a 50‑server BungeeCord network. There are no recurring fees, no per‑server add‑ons, and no hidden costs.

### What You Receive
- The complete BedWars game plugin JAR.
- The BedWarsProxy companion plugin.
- All 33+ add‑ons, fully integrated and ready to use.
- Ranked system backend access and API token.
- Free updates for the current major version.
- **24/7 priority support** via Discord or Bale.

### Support Promise
When an issue arises on your live network, you do not file tickets and hope for a reply. You speak directly with the developer — the person who wrote every line of code. Your uptime is our reputation.

---

## Roadmap

- **Private Games** – invite‑only matches with full host controls (kick, map selection, team size).
- **Continuous Performance Upgrades** – further async offloading, profiling for 3000+ concurrent players.
- **Expanded API** – additional events, hooks, and comprehensive Javadoc documentation.

---

<p align="center">
  <a href="https://debug.nerotek.net"><strong>Connect to the demo: debug.nerotek.net</strong></a>
</p>
