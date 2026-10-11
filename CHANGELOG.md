# Changelog\n\n## 1.1.7 — experimental, pending build and game test\n\n- Updated MelonLoader mod version and project version to 1.1.7.\n- Preserved original creator attribution alongside compatibility maintainer.\n- Implemented an **experimental** Oscar in-game daily report using the v0.4.7 `MessagingManager.SendMessage_Server` and `MSGConversation.ConversationId`.\n- Log output remains the fallback and ledger resets even if phone delivery fails.\n- Phone compatibility and message formatting are **not yet validated**.\n

## 1.1.6 compatibility work — experimental, unreleased

Target: Schedule I **0.4.7f12**, IL2CPP.

### Implemented
- Restore manager startup with a scene-based retry after the loading-screen hook stopped triggering reliably.
- Guard NPC ID lookup to avoid null-reference exceptions during scene startup.
- Delay save-key preference access and callbacks until gameplay services are ready.
- Replace the outdated `MessagingManager.SendMessage` call with MelonLoader log output to keep the daily ledger running.
- Preserve original-author credit while adding the compatibility maintainer.
- Produce an expanded per-day report with property and item breakdown, undiscounted price, savings, charged totals, and cash/bank totals.

### Verified
- The previous startup-fix build initialized successfully and logged numerous automatic restocks in an October 11, 2026 v0.4.7f12 session.
- Daily reporting before the expanded report change was logged successfully.

### Pending
- Compile and validate the expanded daily report and author metadata.
- Restore Oscar's in-game phone message using the new messaging API without introducing runtime failures.
- Audit multiplayer message sender authorization.
- Validate discount settings and nonzero charge scenarios.
- Test save/reload, multiplayer host/client, and scene transitions.

## 1.1.5 upstream
Original functionality from [lasersquid](https://github.com/lasersquid/Sched1AutoRestockMod). See upstream release history for its earlier versions.
