# AutoRestock v1.1.7 testing checklist

**Target:** Schedule I v0.4.7f12, IL2CPP, MelonLoader v0.7.3 Open-Beta.

## Setup

1. Back up the game save and existing AutoRestock DLL.
2. Install one copy of the newly compiled `AutoRestockIL2CPP.dll`.
3. Confirm the in-game mod manager shows version **1.1.7** and credits **lasersquid & AnasaAyatan**.

## Functional checks

- [x] Manager initializes after a save is loaded.
- [x] Automatic restocking occurs on the tested game build.
- [x] A detailed report is generated at an in-game day transition.
- [x] Oscar sends the report to the in-game phone.
- [x] The same report is available in MelonLoader's log.
- [ ] Validate both cash and bank purchases with nonzero charges.
- [ ] Check multiple discount configurations and their financial totals.
- [ ] Verify save, exit to menu, reload and another day transition without duplicate messages.
- [ ] Verify an empty-ledger day.
- [ ] Test multiplayer host/client behavior with authorized players.
- [ ] Recheck compatibility after future game updates.

## Confirmed test: October 11, 2026

The v1.1.7 session recorded 144 transactions, 2,590 restocked units, $31,100 list value and $0 charged under an intentionally configured full discount. The log recorded successful phone-message submission and the tester confirmed the message appeared in-game.

## Reporting issues

Provide the game version, MelonLoader version, AutoRestock version, reproduction steps and a redacted recent `MelonLoader/Logs` file. Do not share account credentials or game saves.
