# BedWars

A high-performance, feature-rich BedWars plugin for Minecraft 1.8.8, exclusively developed and maintained by Nerotek01. Inspired by Hypixel BedWars, this plugin delivers a complete competitive BedWars experience with cosmetics, ranked play, replays, statistics, and extensive customization.

## Features

### Core Gameplay
- Full BedWars game loop: waiting, starting, playing, restarting
- Multiple game modes: Solo, Doubles, Triples, Squads (configurable)
- Team management with automatic assignment and balanced team distribution
- Bed destruction mechanics with respawn disabling
- Generator system (iron, gold, diamond, emerald) with tier-based upgrades
- Shop system with quick-buy and category-based purchasing
- Upgrade system (sharpened swords, protection, haste, heal pool, dragon buff)
- Special items (fireballs, TNT, ender pearls, bridge eggs, knockback sticks, etc.)
- Re-spawn protection and invulnerability windows
- Spectator mode with teleporter GUI and free-camera support

### Server Modes
- MULTIARENA: multiple arenas running on a single server
- BUNGEE: one arena per server with proxy-based scaling
- SHARED: arena world running alongside a main lobby world
- Auto-scale: automatically clone arenas when player demand is high

### Arena Management
- In-game setup session with guided arena creation
- Arena cloning and auto-scaling for high-traffic periods
- Arena groups for organizing maps by game mode
- SlimeWorldManager integration for fast world reset
- Internal world reset adapter as a fallback
- Build height limits and region protection
- Block break/place restrictions with whitelist support

### Commands
All commands are registered dynamically at runtime (not declared in plugin.yml).

| Command | Description |
|---------|-------------|
| /bw | Main BedWars command (opens GUI, stats, etc.) |
| /bw join [arena] | Join an arena or pick a random one |
| /bw leave | Leave current arena |
| /bw spawn | Return to lobby spawn |
| /bw start | Force-start the game (requires permission) |
| /bw stats [player] | View player statistics (requires stats-menu addon) |
| /bw level add/set/remove <player> <amount> | Administer player levels (requires bedwars.level) |
| /bw quickbuy | Open quick-buy configuration (requires quick-buy addon) |
| /bw token | Token economy management (requires token-economy addon) |
| /bw teleporter | Open spectator teleporter |
| /bw tph <player> / confirm / cancel | Staff teleport a player out of arena (requires bw.tph) |
| /bw ranked | Open ranked matchmaking menu (requires ranked addon) |
| /bw replay | Replay system commands (requires replay addon) |
| /bw quests | View daily quests (requires quests addon) |
| /bw setuparena | Start arena setup session |
| /bw enablearena | Enable an arena |
| /bw disablearena | Disable an arena |
| /bw clonearena | Clone an existing arena |
| /bw arenagroup | Manage arena groups |
| /bw build | Toggle build mode in arena |
| /bw setlobby | Set the lobby location |
| /bw npc | Manage join NPCs |
| /bw reload | Reload plugin configuration |
| /bw cosmetics | Open cosmetics menu |
| /stats [player] | Standalone stats command |
| /party | Party management commands |
| /shout | Send a global shout message |
| /rejoin | Rejoin a disconnected game |
| /leave | Leave current game |
| /spectate | Spectate an ongoing game |
| /teleporter | Spectator teleporter shortcut |
| /replay | Replay viewer command |

### Permissions
All permissions are registered dynamically at runtime through the centralized Permissions and CosmeticsPermissions classes.

#### Core Permissions
| Permission | Default | Description |
|------------|---------|-------------|
| bw.* | op | Access to all BedWars commands |
| bw.forcestart | op | Force-start a game |
| bw.setup | op | Create and edit arenas |
| bw.groups | op | Manage arena groups |
| bw.build | op | Toggle build mode |
| bw.clone | op | Clone arenas |
| bw.enableRotation | op | Enable/disable arenas |
| bw.npc | op | Manage join NPCs |
| bw.cmd.bypass | op | Bypass blocked-command restrictions |
| bw.shout | true | Use the /shout command |
| bw.shout.bypass | op | Bypass shout cooldown |
| bw.tph | true | Use /bw tph |
| bw.party | true | Use party commands |
| bw.vip | false | VIP slot join priority |
| bw.chatcolor | op | Use colored chat in arena |
| bedwars.admin | op | Administrative access |
| bedwars.economy | op | Economy management |
| bedwars.level | true | Level system access |
| bedwars.stats.others | true | View other players stats |
| bedwars.proxydebug | op | Proxy debug command |
| bedwars.ranked.join | true | Join ranked queues |
| bedwars.ranked.tournament.start | op | Start a tournament |
| bedwars.ranked.debug | op | Ranked debug commands |
| bedwars.replay.setwaiting | op | Set replay waiting room |
| bedwars.start.debug | op | Debug start logic |

#### Cosmetics Permissions
| Permission | Default | Description |
|------------|---------|-------------|
| bedwars.cosmetics.use | true | Open the cosmetics menu |
| bedwars.cosmetics.admin | op | Administer cosmetics (reload, set) |
| bedwars.cosmetics.preview | true | Right-click to preview cosmetics |
| beddestroy.* | false | All bed-destroy effects |
| deathcry.* | false | All death cries |
| finalkilleffect.* | false | All final-kill effects |
| glyph.* | false | All glyphs |
| killmessage.* | false | All kill messages |
| projectiletrail.* | false | All projectile trails |
| shopkeeperskin.* | false | All shopkeeper skins |
| spray.* | false | All sprays |
| victorydance.* | false | All victory dances |
| woodskin.* | false | All wood skins |
| islandtopper.* | false | All island toppers |

Individual cosmetics use the format `<category>.<identifier>` (for example `victorydance.dragon-rider`, `glyph.gold`, `spray.creeper`). These are registered dynamically by the CosmeticsPermissions class.

### Conditional Commands
The following commands are only registered when their prerequisite is met. If the prerequisite is not satisfied, the command will not exist on the server.

| Command | Prerequisite |
|---------|--------------|
| /bw quickbuy | quick-buy addon enabled |
| /bw token | token-economy addon enabled |
| /bw ranked | ranked addon enabled AND bot token configured |
| /bw replay | replay addon enabled |
| /bw quests | quests addon enabled |
| /bw cosmetics | cosmetics addon enabled |
| /bw stats | stats-menu addon enabled |
| /bw gui, /bw map-gui | map-selector addon enabled |
| /bw leaderboard | leaderboard addon enabled |
| /bw hotbar | hotbar-manager addon enabled |
| /bw npc | Citizens plugin installed AND server type is not BUNGEE |
| /bw setlobby | server type is not BUNGEE |
| /map | map-command addon enabled |
| /shout | not already registered by another plugin |
| /leave | server type is not BUNGEE OR not already registered |
| /spectate | GENERAL_ENABLE_SPECTATE_CMD config is true |
| /party | parties allowed AND party cmd enabled in config |
| /replay (top-level) | replay addon enabled AND not already registered |
| /teleporter | not already registered by another plugin |
| /rejoin | not already registered by another plugin |

### Cosmetics System
Eleven cosmetic categories, each with many items:
- Bed Break Effects
- Death Cries
- Final Kill Effects
- Glyphs
- Kill Messages
- Projectile Trails
- ShopKeeper Skins
- Sprays
- Victory Dances
- Wood Skins
- Island Toppers

Cosmetics support rarity tiers, vault-based pricing, preview mode, and per-player owned-data persistence.

### Addons
The plugin ships with a modular addon system. Each addon can be enabled or disabled individually in the configuration.

- Anti-AFK: detects and penalizes inactive players
- Anti-Drop: prevents dropping restricted items
- Arena Start Message: announces game start
- Boss Bar: in-game boss bar progress display
- Compass: target-tracking compass for spectators
- Cosmetics: full cosmetics system
- Deposit: resource deposit listeners
- Gen Split: split generator drops among nearby players
- Hotbar Manager: customize hotbar layout and sword enchant renaming
- Leaderboards: persistent leaderboard with holograms
- Map Selector: GUI-based map and group selection
- Play Again: quick re-queue after game end
- Quick Buy: customizable quick-buy bar
- Ranked: competitive ranked matchmaking with WebSocket integration
- Replay: full game replay recording and playback
- Reward Summary: post-game reward breakdown
- Spectator Options: spectator-specific settings
- Stats Menu: detailed statistics GUI
- Team Selector: pre-game team picking
- Quests: daily and weekly quest system
- Voidless: voidless game mode variant
- World Border: enforce arena boundaries
- Height Limit: build height enforcement
- Water Height Limit: water placement restriction
- Invisibility Footsteps: hide footstep particles for invisible players
- Level Bar: XP level bar integration
- Leave Delay: configurable post-game leave delay
- Sponge: sponge block absorption handling

### Database Support
- MongoDB: primary persistent storage for player data, stats, and cosmetics
- Redis: optional caching layer for cross-server data
- Leaderboard cache with automatic refresh

### Statistics
- Comprehensive per-game statistics tracking
- Persistent player statistics (kills, deaths, wins, losses, beds broken, etc.)
- Leaderboard with hologram display
- Statistics menu GUI with sortable columns
- PlaceholderAPI integration for stats display

### Replay System
- Full game replay recording
- Replay playback with timeline scrubbing
- Replay viewer GUI
- Replay lobby removal for clean replay viewing
- Automatic replay cleanup and retention

### Ranked System
- Competitive ranked matchmaking
- Player profile management
- WebSocket integration with bot backend
- Tournament support with NPC entry points
- Season rules hologram display
- Ranked leaderboard
- Shop and upgrade restrictions for ranked fairness

### Party System
- Internal party system
- Parties plugin integration (AlessioDP)
- Party chat and party join coordination

### PlaceholderAPI Integration
The plugin registers a rich set of PlaceholderAPI placeholders for stats, level, ranked rating, cosmetics, and more.

### Configuration
- Main config: config.yml
- Generators config: generators.yml
- Sound config: sound.yml
- Levels config: levels_defaults.yml
- Language files: per-locale message files
- Addon configs: per-addon YAML files in Addons/
- Cosmetics configs: per-category YAML files

### Server Compatibility
- Requires Minecraft 1.8.8
- Requires PlaceholderAPI
- Optional soft-depends: Vault, SlimeWorldManager, Citizens, Parties
- Supports Spigot, Paper, and PandaSpigot

## Installation
1. Download the latest BedWars.jar from the Releases page.
2. Place the JAR in your server plugins folder.
3. Start the server to generate default configuration files.
4. Configure plugins/BedWars/Configs/config.yml as needed.
5. Set up at least one arena using /bw setuparena.
6. Restart the server.

## Building From Source
Requirements: Java 21 and Gradle 8.10+ (wrapper included).

```bash
git clone https://github.com/Nerotek01/Bed-Wars.git
cd Bed-Wars
./gradlew :bedwars_plugin:shadowJar
```

The compiled JAR will be at bedwars_plugin/build/libs/BedWars-2.1.7.jar (unobfuscated) or BedWars-2.1.7-obf.jar (ProGuard-obfuscated, for distribution).

## Project Structure
The project is a multi-module Gradle build using Kotlin DSL:

- bedwars_api: public API interfaces and shared types
- versionsupport_common: cross-version listeners and helpers
- versionsupport_1_8_R3: NMS-specific code for Minecraft 1.8.8
- resetadapter_slime: SlimeWorldManager integration for fast arena reset
- bedwars_plugin: main plugin module (depends on all above)

Build configuration lives in:
- settings.gradle.kts: module declarations and plugin management
- build.gradle.kts: root build script with shared repositories, Java 21 toolchain, and compiler options
- gradle.properties: daemon JVM args, parallel builds, JDK installation path
- gradle/wrapper/: Gradle wrapper for reproducible builds
- bedwars_plugin/build.gradle.kts: Shadow plugin configuration, relocations, and resource filtering for plugin.yml version substitution

## Version
Current version: 2.1.7

## Author
Exclusively developed and maintained by Nerotek01.
