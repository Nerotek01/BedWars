<!-- PROJECT SHIELDS -->
[![Spigot](https://img.shields.io/badge/Spigot-1.8.8-orange.svg)](https://www.spigotmc.org/)
[![Paper](https://img.shields.io/badge/Paper-supported-blue.svg)](https://papermc.io/)
[![License](https://img.shields.io/badge/License-All_Rights_Reserved-red.svg)](LICENSE)
[![Discord](https://img.shields.io/discord/your-discord-id?color=7289da&label=discord)](https://discord.gg/yourserver)

<br />
<p align="center">
  <h1 align="center">⚔️ BedWars · Ultimate Edition</h1>
  <p align="center">
    The most feature‑rich, optimised, and modular <strong>BedWars</strong> plugin for Minecraft 1.8.8 servers.
    <br />
    <a href="#-features"><strong>Explore the features »</strong></a>
    <br />
    <br />
    <a href="#-installation">Installation</a>
    ·
    <a href="#-commands--permissions">Commands</a>
    ·
    <a href="#-addons">Add‑ons</a>
    ·
    <a href="#-api">API</a>
  </p>
</p>

---

## 📖 Overview

**BedWars Ultimate Edition** is a complete, self‑contained BedWars solution designed for **1.8.8 Spigot/Paper** servers.  
It supports every game mode you need – from classic **Multi‑Arena** setups to large‑scale **BungeeCord networks with auto‑scaling**.  

Everything is built with performance, extensibility and maintainability in mind:
- Asynchronous database operations (MongoDB / SQLite / Redis)
- Lazy chunk loading and world restoring with **SlimeWorldManager**
- **30+ toggleable add‑ons** that you can enable/disable in a single config file
- Full PlaceholderAPI integration, internal token economy, ranked mode, and a public Java API

---

## ✨ Features

### 🎮 Core gameplay
- **Solo, Doubles, Triples & Quads** – Configure team sizes per arena
- **BungeeCord & Multi‑Arena** – Run one arena per server or many
- **Auto‑scale** – Dynamically spin up new servers as demand grows
- **Map reset system** – Built‑in world restore (supports SlimeWorldManager for instant resets)
- **Generators & upgrades** – Diamond, emerald, and team‑specific generator tiers
- **Team upgrades** – Sharpness, Protection, Haste, Heal Pool, Dragon Buff …
- **Shop** – Fully configurable quick‑buy slots, potions, specials (Fireball, TNT, Egg Bridge …)
- **Spectator system** – Fly around, teleport to players, spectator options add‑on
- **Rejoin** – Players can rejoin an ongoing game after disconnect
- **AFK kick** – Automatic detection and removal

### 🧩 Extras (built‑in, always on)
- **Lobby & arenas worlds** correctly separated
- **Voidless** / water height limit / adventure mode toggles
- **Item deposit** (with hologram chests)
- **Invisibility footsteps & custom invisibility handling**
- **World border enforcement**, TNT protection
- **Player level bar & XP progression**
- **Chat formatting**, shout command
- **Sidebar (scoreboard)** – works on all 1.8.8 builds

---

## 📦 Requirements

| Software                  | Version       | Required?   |
|---------------------------|---------------|-------------|
| **Spigot / Paper**        | 1.8.8         | ✅ Mandatory |
| **PlaceholderAPI**        | Latest        | ✅ Mandatory |
| **MongoDB**               | 4.0+          | ⚠️ Primary (fallback to SQLite exists) |
| **Redis**                 | 6.0+          | ⚠️ Optional (used for cross‑server data) |
| **SlimeWorldManager**     | 2.2.1+        | ❌ Optional (faster map resets) |
| **Parties**               | Latest        | ❌ Optional (party system) |

> ❗ The plugin **will not start** without PlaceholderAPI.  
> MongoDB is strongly recommended – SQLite is only a fallback for single‑server testing.

---

## 🚀 Installation

1. **Stop your server**
2. Place `BedWars.jar` in the `plugins/` folder
3. Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) and run `/papi ecloud download bedwars` (our expansion)
4. Start the server – the plugin will generate all configuration files
5. **Edit `config.yml`**:
   - Set `serverType` (`MULTIARENA`, `BUNGEE`, `SHARED`)
   - Configure your database credentials under `database.mongo`
   - Set the lobby world name and location
6. Create arenas using `/bw setup` (interactive setup)
7. (Optional) Install **SlimeWorldManager** and link it in the config
8. Restart the server and enjoy!

---

## ⚙️ Configuration

The plugin uses a **modular configuration system**. All files are stored in `plugins/BedWars/`:

| File / Folder          | Purpose                                           |
|------------------------|---------------------------------------------------|
| `config.yml`           | Global settings, database, server type            |
| `generators.yml`       | Generator tiers, speeds, and resources            |
| `shop.yml`             | Shop categories, prices, quick‑buy defaults       |
| `addons.yml`           | Enable/disable every single add‑on                |
| `language/*.yml`       | All messages (multi‑language support)             |
| `levels.yml`           | Player XP requirements per level                  |
| `money.yml`            | Token reward rules                                |
| `ranked.yml`           | Ranked mode API keys & settings                   |
| `Arenas/`              | One `.yml` file per arena                         |

---

## 🧱 Commands & Permissions

### `/bw` – Main command (alias: `/bedwars`)
| Subcommand               | Description                        | Permission                              |
|--------------------------|------------------------------------|-----------------------------------------|
| `setup`                  | Create / modify an arena           | `bw.admin`                              |
| `lobby`                  | Set the lobby location             | `bw.admin`                              |
| `join <arena>`           | Join a specific arena              | `bw.player`                             |
| `leave`                  | Leave the current game             | `bw.player`                             |
| `rejoin`                 | Rejoin the last game               | `bw.player`                             |
| `shout`                  | Send a message to all players      | `bw.player`                             |
| `spectate <player>`      | Spectate an ongoing game           | `bw.spectate`                           |
| `map`                    | Vote for the next map              | `bw.player`                             |
| `compass`                | Open the compass tracker menu      | `bw.player`                             |
| `process`                | Debug command                      | `bw.admin`                              |
| `stats [player]`         | View player statistics             | `bw.player`                             |
| `party`                  | Party management (if enabled)      | `bw.party`                              |

> **Note:** All permissions are autogenerated. Check `plugin.yml` for the full list.

---

## 🔌 Add‑ons (30+)

Every add‑on can be **turned on/off individually** inside `addons.yml`.  
This is the full list extracted from your main class:

<details open>
<summary><strong>Click to expand the add‑on catalogue</strong></summary>

| Add‑on                   | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Ranked**               | Competitive ranked games with ELO, web‑socket API, tournaments (NPCs)      |
| **Play Again**           | Quick “Play Again” item after a game ends                                   |
| **Team Selector**         | Interactive GUI to choose your team before the game starts                  |
| **Spectator Options**     | Speed, night vision toggle, auto‑teleport while spectating                  |
| **Compass**               | Tracker compass that points to nearest enemy / team                         |
| **Quick Buy**             | Customisable hotbar shop for fast purchases                                 |
| **Arena Start Message**   | Broadcasts a title/subtitle when the game starts                            |
| **Reward Summary**        | Detailed breakdown of earned rewards after a match                          |
| **Voidless**              | Prevents void kills – teleports players back to their base                  |
| **BossBar**               | Persistent boss bar showing game timer / team status                        |
| **Hotbar Manager**        | Automatically places correct tools in the hotbar (sword, blocks, etc.)      |
| **Stats Menu**            | Interactive GUI displaying personal and global stats                        |
| **Map Selector**          | Lets players vote for the next map from a pool                              |
| **Leaderboard**           | Holographic top‑player leaderboard in the lobby                             |
| **Water Height Limit**    | Restricts placing water above a certain Y level                             |
| **Adventure Mode**        | Forces adventure mode in the arena to prevent breaking blocks               |
| **Anti Drop**             | Prevents item dropping in the arena (except for certain items)              |
| **Gen Split**             | Splits generator drops equally among teammates standing on the generator    |
| **Height Limit Notifier** | Warns players when they reach the build limit                               |
| **Invisibility Footsteps**| Shows footstep particles for invisible players                              |
| **Deposit**               | Deposit resources into a team chest (with hologram)                         |
| **Level Bar**             | XP bar showing player level progress                                        |
| **Sponge**                | Adds sponge mechanics (remove water around sponge)                          |
| **Token Economy**         | Internal coin system (no Vault needed) – earn and spend tokens              |

</details>

---

## 🗄️ Database & Performance

### Database
- **Primary:** MongoDB – stores player stats, quick‑buy layouts, levels, and ranked data.
- **Fallback:** SQLite – automatically activated if MongoDB is disabled or unreachable.
- **Redis** – used for cross‑server stats synchronisation and real‑time leaderboard updates.

### Optimisations
- **Generator rotation** runs every 120 ticks (configurable) to reduce CPU load.
- **Chunk loading** is handled lazily to keep TPS stable.
- **World reset** is performed asynchronously with SlimeWorldManager when available.
- **Async tasks** for database I/O, web‑socket communication (ranked), and lobby ping.
- **Ghost entity cleanup** – all monsters are removed from lobby worlds.

---

## 📦 Public API

The plugin exposes a complete Java API so you can hook into it from your own plugins.

```java
// Get the API instance
BedWars api = BedWars.getAPI();

// Access an arena
IArena arena = api.getArenaByName("solo_01");

// Join a player to a queue
BedWars.joinQueue(player);

// Get ranked stats
Map<String, Object> stats = BedWars.getRankedStats(player);
