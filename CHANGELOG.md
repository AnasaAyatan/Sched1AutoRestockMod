# Changelog

## v1.1.7 — Schedule I 0.4.7 compatibility update

**Verified on October 11, 2026** with Schedule I v0.4.7f12 (IL2CPP) and MelonLoader v0.7.3 Open-Beta.

- Updated the MelonLoader metadata and project version to **1.1.7**.
- Preserved credit to original creator **lasersquid** and added compatibility maintainer **AnasaAyatan**.
- Added an itemized daily restocking report including purchases, unit counts, list value, calculated savings, totals by property, amount charged, and cash/bank breakdown.
- Restored Oscar's in-game report through the updated conversation messaging API.
- Kept the receipt in the MelonLoader log as a fallback.
- Verified restocking activity, day-transition report generation, and actual in-game message delivery.

**Testing scope:** one confirmed v0.4.7f12 game session. Multiplayer, Mono, future game builds, and all price/discount configurations remain outside the verified scope.

## v1.1.6 — startup compatibility work

- Added scene-based retry when the old loading-screen initialization callback no longer starts the manager reliably.
- Guarded NPC identification and save-folder lookups during gameplay initialization.
- Delayed event callbacks until initialization succeeds.
- Temporarily switched daily receipts to log output while adapting to the messaging API changes.

## Original project

AutoRestock was originally created by [lasersquid](https://github.com/lasersquid/Sched1AutoRestockMod). This repository contains an unofficial compatibility update.
