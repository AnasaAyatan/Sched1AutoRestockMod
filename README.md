# AutoRestock — Schedule I v0.4.7 Compatibility

An unofficial, community-maintained update of **AutoRestock**, built for **Schedule I v0.4.7f12 (IL2CPP)**.

**Version:** 1.1.7  
**Original creator:** [lasersquid](https://github.com/lasersquid/Sched1AutoRestockMod)  
**Compatibility maintenance:** [AnasaAyatan](https://github.com/AnasaAyatan/Sched1AutoRestockMod)

> This is a compatibility fork, not an official release by the original creator. Please respect the original project's redistribution permissions before repackaging or publishing binaries.

## Features

- Automatically restocks supported empty storage and production slots.
- Uses the existing restocking configuration, inventory and payment logic.
- Groups daily purchases by property and item.
- Sends a detailed daily business report through **Oscar's in-game phone conversation**.
- Includes purchased quantities, list values, calculated discounts, actual charges, and cash/bank totals.
- Writes a copy of the daily report to the MelonLoader log as a fallback.
- Adds safeguards and a scene-based retry for initialization on Schedule I v0.4.7.

## Daily business report

At the in-game day transition, Oscar sends a report covering the previous day's restocking purchases. An example with illustrative prices:

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

The report calculates savings from the recorded list value minus the actual charged amount. **Reporting does not change the price or discount settings.** A discount setting of `1` yielded a 100% discount in the verified test; that was intentionally configured by the tester.

## Compatibility and verification

| Component | Status |
| --- | --- |
| Schedule I v0.4.7f12, IL2CPP | Tested |
| MelonLoader v0.7.3 Open-Beta | Tested |
| Automatic restocking | Confirmed in-game |
| Daily detailed report | Confirmed in log |
| Oscar phone message | Confirmed in-game |
| Mono branch, multiplayer, later game builds | Not yet verified |

**October 11, 2026 test:** AutoRestock v1.1.7 initialized, performed restocking and delivered Oscar's message in-game. The test day's report contained 144 transactions, 2,590 units and $31,100 in pre-discount list value; the configured full discount resulted in $0 charged. These are test-session observations, not performance guarantees.

## Build from source (Windows, IL2CPP)

You need the .NET SDK, MelonLoader, and IL2CPP reference assemblies generated from **your own game installation**.

1. Clone this repository and switch to the `fix/schedule-i-0.4.7` branch.
2. Place the required game-generated references in `AutoRestock/il2cpp_libs/`, as specified by `AutoRestock.csproj`.
3. From the repository root, build without the optional packaging/deployment scripts:

```powershell
dotnet build .\AutoRestock\AutoRestock.csproj -c IL2CPP -p:SkipModPackaging=true
```

4. The output is `AutoRestock/bin/IL2CPP/net6/AutoRestockIL2CPP.dll`.

Do not commit generated game assemblies, game saves, personal configuration files or build artifacts.

## Installation

1. Back up your current game save and AutoRestock DLL.
2. Close Schedule I. Disable any previous AutoRestock installation in Vortex and deploy that change.
3. Copy `AutoRestockIL2CPP.dll` to the game's `Mods` folder, ensuring only one active AutoRestock DLL is installed.
4. Launch the game and verify AutoRestock displays **v1.1.7** with credit to **lasersquid & AnasaAyatan**.

## Troubleshooting

Check the newest file in `MelonLoader/Logs`.

- `AutoRestock manager initialized.` confirms initialization.
- `Restocking ...` entries show attempted transactions.
- `Oscar daily report submitted to phone messaging.` confirms message submission.
- If the phone report does not appear, check the logged daily receipt and errors.

For issues, include the exact game version, reproduction steps and a redacted MelonLoader log.

## Known limitations

The compatibility update has been validated on **v0.4.7f12**, not every game branch or future update. Multiplayer sender validation and additional discount scenarios have not been comprehensively tested.

## Development

- [Changelog](CHANGELOG.md)
- [Testing checklist](docs/TESTING.md)
- [Compatibility branch](https://github.com/AnasaAyatan/Sched1AutoRestockMod/tree/fix/schedule-i-0.4.7)
- [Original source](https://github.com/lasersquid/Sched1AutoRestockMod)

AutoRestock's original design and source are credited to **lasersquid**. The v0.4.7 compatibility update and detailed daily reporting are maintained by **AnasaAyatan**.
