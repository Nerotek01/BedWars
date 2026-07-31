# BedWars Changelog

## v2.1.6

### Critical Fix: Join Lockout
- Fixed critical bug where players could not join any arena when all arenas are ranked
- Restored admin bypass in canBypassRankedRestriction (OPs and admins can join ranked arenas for testing)
- Added ranked fallback in handleRandomJoin - if no non-ranked arenas exist, ranked arenas are used as fallback
- Fixed BedWarsAdapter.onArenaJoin to allow OPs and admins through the event listener

## v2.1.5

### Tab-Completion Fixes
- Excluded clone arenas from all tab-completion (/bw join map, /bw join forcejoin, /bw disablearena, /bw enablearena, /bw clonearena)
- Restricted /bw join forcejoin all world argument to only suggest the lobby world

## v2.1.4

### Ranked Access Control and Clone Cleanup
- Blocked all manual entry to ranked arenas for regular players (bot-only access)
- Added aggressive clone cleanup on server shutdown (deletes all clones including those with active players)
- Added migration of existing arena config locations to block-level precision
- Made /bw arenagroup help messages interactive with hover and click

## v2.1.3

### ProGuard VerifyError Fix
- Fixed third VerifyError by adding all JDK jmods as ProGuard libraryjars
- ProGuard can now resolve javax.management class hierarchy for multi-catch handlers

## v2.1.2

### ProGuard and Bug Fixes
- Fixed second VerifyError by preserving all third-party library bytecode
- Fixed InvisibilityFootsteps cross-world crash
- Fixed Voidless NPE on null group
- Fixed ArenaStartAnnouncer NPE on null group/prefix
- Fixed WorldBorderListener stale per-player cache on arena leave
- Fixed RankedQueueManager never removing quitters from queue

## v2.1.1

### ProGuard StackMapTable Fix
- Fixed first VerifyError by removing -dontpreverify from ProGuard config
- Applied 5 tick-hot path optimizations for high arena/player count

## v2.1.0

### Gradle Migration and ProGuard
- Migrated build system from Maven to Gradle (Kotlin DSL)
- Added ProGuard obfuscation task with comprehensive keep rules
- Fixed slime world file accumulation (orphan cleanup on startup)
- Cleaned up arena config format (removed placeholder keys, legacy key migration)
- Added random lobby spawn feature
- Fixed hotbar item pickup routing to upper inventory
- Fixed /bw start command feedback for already-playing state
- Fixed deposit for non-stackable items (swords, tools)

## v2.0.0

### Major Release: Gradle Migration
- Migrated from Maven to Gradle Kotlin DSL
- Multi-module Gradle build with Shadow plugin
- Java 21 toolchain enforcement
- ProGuard obfuscation for anti-crack protection
- Slime world orphan cleanup
- Arena config format cleanup with block-level location coordinates
