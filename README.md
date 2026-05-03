# BedWars · Ultimate Edition

> The most advanced, performance‑focused BedWars plugin for Minecraft 1.8.8 Spigot / Paper.  
> Built for large networks and demanding servers that refuse to compromise on quality.  
> **Tested and stable with over 2000 players online simultaneously.**  
> **100% configurable – every mechanic, message, and add‑on can be adjusted to fit your server perfectly.**

---

## Table of Contents

- [Why BedWars Ultimate?](#-why-bedwars-ultimate)
- [Feature Overview](#-feature-overview)
- [Ranked System (Full)](#-ranked-system-full)
- [Add‑ons](#-add‑ons)
- [Commands & Permissions (Complete Reference)](#-commands--permissions-complete-reference)
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

When you choose BedWars Ultimate, you choose a plugin that doesn't just work—it excels, even when your server is packed full.

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

## Commands & Permissions (Complete Reference)

Main command: `/bw` (alias `/bedwars`)

### Player Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw join <map/group/random>` | Join a game by map name, arena group, or randomly | `bw.player` |
| `/bw join ranked` | Join the ranked queue | `bw.player` |
| `/bw join forcejoin <player> [arena]` | Force a player into a specific arena (admin only) | `bw.admin` |
| `/bw leave` | Leave the current game | `bw.player` |
| `/bw rejoin` | Rejoin the last game if still in progress | `bw.player` |
| `/bw shout <message>` | Send a message to all players in the game | `bw.player` |
| `/bw spectate <player>` | Spectate a specific player | `bw.spectate` |
| `/bw map` | Vote for the next map | `bw.player` |
| `/bw stats [player]` | View your own or another player's statistics | `bw.player` |
| `/bw compass` | Open the enemy tracker compass menu | `bw.player` |
| `/bw gui [group]` | Open the map selector GUI | `bw.player` |
| `/bw ranked` | Open the ranked menu (inside tournament arenas) | `bw.player` |
| `/bw quickbuy` | Customize your quick‑buy slots | `bw.player` |
| `/bw tokens [player]` | Check token balance (yours or another player's) | `bw.player` |
| `/bw level <set/add/remove> <player> <amount>` | Manage player levels (admin only) | `bw.admin` |
| `/bw hotbar menu` | Open the hotbar manager GUI | `bw.player` |
| `/map` | Shortcut to map voting | `bw.player` |
| `/leave` | Leave the current game (if not overridden by another plugin) | `bw.player` |
| `/shout <message>` | Shortcut for shout chat | `bw.player` |
| `/spectate <player>` | Shortcut to spectate a player | `bw.spectate` |
| `/stats` | Shortcut to view your stats | `bw.player` |
| `/statistics` | Admin statistics view | `bw.admin` |

### Admin Commands (Setup & Management)

| Command | Purpose | Permission |
|---------|---------|------------|
| `/bw setup` | Interactive arena creation wizard | `bw.admin` |
| `/bw lobby` | Set the main lobby spawn point | `bw.admin` |
| `/bw setlobby` | Set the lobby world and spawn location | `bw.admin` |
| `/bw setuparena <name>` | Setup a new arena | `bw.admin` |
| `/bw enablearena <name>` | Enable a disabled arena | `bw.admin` |
| `/bw disablearena <name>` | Disable an arena | `bw.admin` |
| `/bw clonearena <source> <target>` | Clone an existing arena configuration | `bw.admin` |
| `/bw arenagroup <arena> <group>` | Set the group of an arena | `bw.admin` |
| `/bw build` | Toggle build mode for arena setup | `bw.admin` |
| `/bw setwaitingspawn` | Set the waiting lobby spawn for an arena | `bw.admin` |
| `/bw setspectspawn` | Set the spectator spawn point | `bw.admin` |
| `/bw createteam <name> <color>` | Create a new team in the current setup | `bw.admin` |
| `/bw waitingpos <team>` | Set the waiting position for a team | `bw.admin` |
| `/bw removeteam <name>` | Remove a team from the arena | `bw.admin` |
| `/bw setmaxinteam <amount>` | Set maximum players per team | `bw.admin` |
| `/bw setmaxbuildheight <height>` | Set the maximum build height | `bw.admin` |
| `/bw setspawn <team>` | Set the team spawn point | `bw.admin` |
| `/bw setbed <team>` | Set the team bed location | `bw.admin` |
| `/bw setshop <team>` | Set the team shop location | `bw.admin` |
| `/bw setupgrade <team> <upgrade>` | Set an upgrade station location | `bw.admin` |
| `/bw addgenerator <type> <tier>` | Add a resource generator | `bw.admin` |
| `/bw removegenerator` | Remove a generator (while looking at it) | `bw.admin` |
| `/bw autocreateteams <solo/doubles/triples/quads>` | Auto‑create teams with default colors | `bw.admin` |
| `/bw settype <type>` | Set the arena game type | `bw.admin` |
| `/bw setkilldrops <team>` | Set the kill drops collection point | `bw.admin` |
| `/bw save` | Save the current arena configuration | `bw.admin` |
| `/bw teleporter <team>` | Set a teleporter location | `bw.admin` |
| `/bw start` | Force start the current arena | `bw.admin` |
| `/bw start debug` | Debug force start | `bw.admin` |
| `/bw tph` | Teleportation helper during games (admin only) | `bw.admin` |
| `/bw upgradesmenu` | Open the team upgrades menu (while in game) | `bw.admin` |
| `/bw reload` | Reload plugin configuration | `bw.admin` |
| `/bw reload confirm` | Confirm reload (if pending) | `bw.admin` |
| `/bw reload cancel` | Cancel reload (if pending) | `bw.admin` |
| `/bw npc` | Manage Citizens NPCs (if Citizens is installed) | `bw.admin` |
| `/bw leaderboard` | Manage leaderboard holograms | `bw.admin` |
| `/bw ranked tournament start <arena>` | Start a ranked tournament in a specific arena | `bedwars.ranked.tournament.start` |
| `/bw ranked tournament cancel <arena>` | Cancel an active tournament | `bedwars.ranked.tournament.start` |
| `/bw ranked forcejoin <player> [arena]` | Force a player into ranked | `bedwars.ranked.tournament.start` |

### Permissions Overview

| Permission Node | Access Level |
|-----------------|-------------|
| `bw.player` | All player commands |
| `bw.spectate` | Spectate command access |
| `bw.admin` | All admin and setup commands |
| `bedwars.admin` | Alternative admin permission |
| `bw.*` | Wildcard for all plugin permissions |
| `bedwars.ranked.debug` | Ranked debug features access |
| `bedwars.ranked.tournament.start` | Tournament management commands |

All permissions can be managed through any permissions plugin (LuckPerms, PermissionsEx, etc.).

### Tab Completion

The plugin provides intelligent tab completion for nearly all commands:

- **Arena names** are suggested when using `/bw join`, `/bw enablearena`, etc.
- **Player names** are auto‑completed for `/bw spectate`, `/bw stats`, and forcejoin operations
- **Arena groups** are suggested for `/bw join group` and `/bw gui`
- **Ranked commands** offer context‑sensitive completions for tournaments, forcejoin, etc.
- **Online players** are listed for all player‑targeting commands
- **Reload** command shows confirm/cancel when a reload is pending

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
