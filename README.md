# Project: Ashen Convergence (working title)

A **private, single-player, five-hero, isometric idle action RPG** for Android phone/tablet and desktop browsers. Inspired by the strategic depth of Epic Seven, but with original characters, lore, artwork, rules, and real-time automated movement/combat. This is **not** Classless Dungeon, its idle fork, or a multiplayer game.

## Pillars
1. **Watchable combat:** Five visually distinct heroes navigate compact isometric arenas, move, cast, counter, support, and defeat enemies automatically. Manual intervention is optional, never required for routine farming.
2. **Meaningful builds:** Heroes retain signature identities; weapon masteries, limited talents, equipment sets, and Tactical Directives change how they perform.
3. **Support matters:** Tempo, buffs, debuffs, control, protection, coordination, resource generation, and healing all have measurable value.
4. **Idle-friendly progression:** Auto-repeat, auto-advance, configurable loot rules, and deterministic offline reward settlement. No paid currency or artificial monetization friction.
5. **Original grimdark pixel art:** Large readable sprites, Western gothic science-fantasy silhouettes, dramatic signature abilities, atmospheric environments; no copied Epic Seven or Warhammer assets.
6. **Small, testable increments:** One numbered task per explicit approval; no uncontrolled multi-task implementation.

## World and factions
A dying-star science-fantasy setting. **Astral Concord** (astral gothic), **Iron Foundries** (industrial gothic), **Veiled Communion** (occult gothic). Names, characters, and lore are original. Working title and character names are provisional.

## Initial vertical slice
One isometric arena, five playable heroes (frontline, damage, controller, non-healing tempo support, flex/protector), three enemy archetypes, one boss, full auto-combat, a minimal loot loop, and responsive portrait/desktop presentation. **Do not** start by making 30–40 heroes.

## Repository documents
- `GAME_DESIGN.md` — mechanics and interface contract.
- `TASKS.md` — ordered checkpoints with acceptance criteria.
- `AGENTS.md` — binding one-task-at-a-time instructions for coding agents.
- `PROJECT_STATE.md` — short resumption log, updated after every task.

## Platform and deployment
Browser-first. Verify current ChatGPT Sites build/import/storage requirements before committing to a renderer or hosting architecture. GitHub is source of truth; Sites is the preview/publishing destination. Local-first persistence is required; cross-device sync is optional only after feasibility and cost are verified. **No paid API billing without explicit approval.**

## Out of scope for initial release
Multiplayer, PvP, accounts, real-money purchases, open-world exploration, manually controlled action combat, live-service infrastructure, massive roster, complex physics, and continuous browser-background execution.
