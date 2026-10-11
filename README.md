# AutoRestock — Schedule I compatibility fork

Experimental community-maintained compatibility branch for **Schedule I v0.4.7f12 (IL2CPP)**.

**Original mod:** [lasersquid / Sched1AutoRestockMod](https://github.com/lasersquid/Sched1AutoRestockMod)  
**Compatibility fork:** [AnasaAyatan / Sched1AutoRestockMod](https://github.com/AnasaAyatan/Sched1AutoRestockMod)  
**Credits:** Original design and implementation by **lasersquid**; v0.4.7 compatibility maintenance by **AnasaAyatan**.

> **Development status:** The startup fix and automatic restocking were observed working in the October 11, 2026 game log on v0.4.7f12. The new detailed receipt and combined author metadata have been committed but **not yet compiled or game-tested**. Do not treat this branch as a verified public release.

## Features

- Automatically replenishes supported empty storage and production slots.
- Uses the original mod's funds, pricing, and restocking logic.
- Handles restocking transactions by property.
- Adds fallback startup logic for game v0.4.7 and guards against uninitialized NPC IDs or save identifiers.
- **New experimental daily report:** itemized purchases, property subtotals, unit quantities, undiscounted list prices, savings, charged totals, and cash/bank breakdown. Reports are always written to the **MelonLoader log**; v1.1.7 now also **attempts Oscar's in-game phone delivery** using the updated messaging API, pending compile and runtime validation.

### Example daily report (illustrative figures)

```text
Oscar's daily restocking report - Monday
================================

PROPERTY: Bungalow
  Cuke x20: list $40.00, discount $10.00, paid $30.00
  Property subtotal: 20 units | list $40.00 | saved $10.00 | paid $30.00

DAILY TOTALS
Transactions: 1 | Units purchased: 20
List price: $40.00
Discounts / savings: $10.00
Amount charged: $30.00
Cash: $30.00 (1 transactions)
Bank: $0.00 (0 transactions)
Oscar says thank you for your business!
```

The report uses the existing transaction ledger. **Savings** are calculated as `unitPrice × quantity − totalCost`; this is descriptive accounting, not a change to charges.

## Compatibility

| Component | Status |
| --- | --- |
| Schedule I v0.4.7f12, IL2CPP | Restocking verified in user-provided October 11 log |
| MelonLoader v0.7.3 Open-Beta | Used during the verified test |
| Restocking manager initialization | Verified |
| Detailed daily report | Source updated; testing pending |
| Oscar in-game phone message | v1.1.7 implementation committed; compile/gameplay test pending |
| Mono game branch | Not tested for this compatibility fork |

The October 11 log also showed a separate **AutoLaunder** missing-method error; this fork does not fix other mods.

## Build (Windows, IL2CPP)

Requires the .NET SDK, MelonLoader, and your **own** game-generated IL2CPP reference assemblies. Install and run the game with MelonLoader once to generate assemblies.

1. Clone this repository and check out `fix/schedule-i-0.4.7`.
2. Create `AutoRestock/il2cpp_libs` and copy the referenced assemblies from your local game's `MelonLoader/Il2CppAssemblies`, `MelonLoader/net6`, and any other paths required by the project.
3. Run:

```powershell
dotnet build .\AutoRestock\AutoRestock.csproj -c IL2CPP -p:SkipModPackaging=true
```

4. Find the output at `AutoRestock/bin/IL2CPP/net6/AutoRestockIL2CPP.dll`.

**Do not commit** generated game assemblies, dependencies, binaries, logs, user preferences, or saved games. Do not run the project’s optional `DeployMod.ps1` unless you have reviewed its file-removal behavior.

## Installing and testing

1. Back up your game save and currently installed mod.
2. Close Schedule I, disable the old AutoRestock deployment in Vortex, and deploy that change.
3. Install just the newly compiled `AutoRestockIL2CPP.dll` in the game's `Mods` folder. Ensure only one active copy exists.
4. Launch v0.4.7f12, load a save, and test restocking.
5. Check `MelonLoader/Logs` for `[AutoRestock] AutoRestock manager initialized.`, transaction lines, and the daily receipt after the next in-game day.
6. Report compile/runtime errors with a fresh MelonLoader log, redacting any personal identifiers.

**Known limitations and cautions:** Phone-message delivery uses an experimental v0.4.7 messaging API call; its compile and runtime behavior remain unverified. The original project has peer-to-peer transaction handling; avoid untrusted multiplayer sessions until sender validation has been audited. Test discount settings carefully, as a discount of `1` was observed yielding zero-cost restocks in the user's prior test.

## Project history

- **v1.1.5 (upstream):** Original baseline by lasersquid.
- **v1.1.6 experimental:** IL2CPP v0.4.7 scene fallback, startup guards, replacement of broken receipt message call with log output, and a detailed reporting update pending runtime validation.

- **v1.1.7 experimental:** detailed reporting and attempted Oscar phone delivery with a per-conversation identifier; awaiting testing.\n\nSee [CHANGELOG.md](CHANGELOG.md) for update notes and [docs/TESTING.md](docs/TESTING.md) for a validation checklist. Bug reports and pull requests should target the compatibility branch until the changes are proven stable.

## Original project links

- [Original GitHub source](https://github.com/lasersquid/Sched1AutoRestockMod)
- [Nexus Mods](https://www.nexusmods.com/schedule1/mods/1235)
- [Thunderstore IL2CPP](https://thunderstore.io/c/schedule-i/p/lasersquid/AutoRestockIL2CPP/)
- [Thunderstore Mono](https://thunderstore.io/c/schedule-i/p/lasersquid/AutoRestockMono/)

This fork is an independent compatibility effort and is not an official release of the original mod or the game.
