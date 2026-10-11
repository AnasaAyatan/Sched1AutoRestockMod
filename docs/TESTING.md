# Validation guide — 0.4.7f12

## Before testing
- Back up your game save and installed AutoRestock DLL.
- Confirm Schedule I reports v0.4.7f12 and MelonLoader starts.
- Disable Vortex's old AutoRestock deployment and retain exactly one active DLL.
- Compile from the repair branch with `-p:SkipModPackaging=true`.

## Required tests
1. Load a single-player save. Confirm `AutoRestock manager initialized.` appears once per loaded save.
2. Restock supported inputs at two properties. Confirm item quantities and player balances match the logs.
3. Test both cash and bank transactions. Check amounts deducted.
4. Test discounts of 0 and any other supported configured values; confirm expected totals before publishing.
5. Cross an in-game day boundary. Check the detailed receipt for item quantities, gross list prices, calculated savings, actual charges, property subtotals, and payment method totals.
6. Save, exit to menu, reload, and repeat. Look for duplicate event subscriptions or duplicate reports.
7. Start with an empty ledger and verify the report indicates no purchases.
8. Check for NullReferenceException, MissingMethodException, and errors about empty MelonPreferences identifiers.
9. Separately test host/client multiplayer only in a trusted session; audit sender authorization before wider distribution.

## Expected report behavior
The detailed receipt currently appears in the **MelonLoader log only**. In-game Oscar messaging has not yet been restored. The game's v0.4.7 messaging API must be investigated and tested before enabling phone messages.

## Reporting bugs
Attach the latest `MelonLoader/Logs` file, game version, MelonLoader version, mod version, reproduction steps, expected and actual results, and relevant configuration (with personal information removed).
