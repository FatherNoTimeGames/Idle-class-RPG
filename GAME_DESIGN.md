# Game Design Specification — v0.1

**Status:** planning baseline; tuning numbers are provisional and must live in configuration. This document is for the *Epic Seven-inspired isometric idle ARPG*, **not** the low-poly 3D Classless Dungeon project.

## 1. Core loop
1. Choose five heroes, equipment, talents, and Tactical Directives.
2. Select a PvE stage, arena, boss, or repeat-farm target.
3. Five heroes auto-move, acquire targets, attack, cast, react, and reposition in a compact isometric battlefield.
4. Collect rewards, salvage or equip gear, improve heroes, summon, and advance.
5. Repeat online at accelerated visual speed, or settle eligible offline rewards when returning.

## 2. Combat architecture
- **Five active allies**; enemy counts vary by encounter. No mandatory tank/healer/role slots.
- **Real-time simulation, fixed tick**, deterministic seeded RNG, headless simulation independent from rendering. No turn queue or copied Epic Seven formulas.
- **Auto-attacks** at weapon-dependent intervals. Active abilities have cast time, cooldown, range, targeting, optional global action lock, and resource costs. Interrupts and crowd control operate through explicit state transitions.
- **Spatial rules:** isometric 2D arena coordinates, collision/avoidance, melee reach, projectile travel as needed, AoE shapes, line of sight where meaningful, simple navigation and separation. Favor readable predictable movement over complex physics.
- **Threat:** lightweight target preference/taunt/protection rather than full MMO aggro simulation. Enemy AI should target meaningfully without making five-character auto-play unmanageable.
- **Elements:** original configurable affinity triangle or equivalent; bonuses affect damage and/or status chance, not movement logic.
- **Statuses:** buffs, debuffs, DoT, HoT, barrier, cleanse, dispel, stun, silence, slow, defense break, vulnerability, immunity, taunt. Every status defines duration, stacking, expiration, and immunity interactions.
- **Stats:** HP, Attack, Defense, Speed, Crit Chance, Crit Damage, Effectiveness, Resistance, plus optional role-specific secondary stats. Cap and diminishing-return rules are configurable.
- **Damage:** implement an original tested pipeline: base ability coefficient × effective attack × defense mitigation × element modifier × critical modifier × other additive/multiplicative modifiers; log each stage. Do not hardcode final balance constants.
- **Tempo translation:** Epic Seven-style Combat Readiness and turn manipulation become action speed, cooldown reduction, cast acceleration, bonus actions, and resource generation. Avoid a hidden turn system alongside real-time combat.
- **Counters/dual attacks:** triggered reactions and coordinated follow-ups with internal cooldowns, trigger limits, and loop protection.
- **Empowerment:** shared party resource earned in combat, spent to empower selected skills; all values configurable.
- **Win/fail:** objective completion, full party defeat, timeout, or mission-specific conditions. Simulated time and wall-clock time are distinct.

## 3. Roles and starting party
Roles are descriptors, **not slots**. Supports need not heal.

| Prototype hero | Faction | Function | Signature concept |
|---|---|---|---|
| Solenne Veyra | Astral Concord | Frontline / protector | Shields, intercepts, defensive counter |
| Ashen Marksman | Iron Foundries | Ranged damage / debuff | Precision fire, armor break, priority targeting |
| Furnace Reaver | Iron Foundries | Bruiser / flex | Heavy cleaves, self-sustain, retaliatory attacks |
| Starbound Oracle | Astral Concord | **Non-healing** tempo / enabler | Cooldown acceleration, coordinated attacks, team energy |
| Veilbinder (working name) | Veiled Communion | Control / disruption | Silence, displacement, debuff amplification |

Start with these five only; later expand toward 30–40 heroes after pipeline validation. Every hero has a basic action, two or three signature abilities (active/passive mix), and an ultimate/empowered effect. Exact kits are task-scoped design decisions, not preapproved content expansion.

## 4. Tactical Directives
Each hero has a small **ordered priority list** of condition → action rules (initially up to five; extensible later). Evaluate at safe decision points, not every render frame. Examples: interrupt dangerous cast; shield ally below HP threshold; apply defense break if absent; focus boss add; use basic attack otherwise.
- Ship with usable presets (balanced, aggressive, defensive, support) and a robust fallback action.
- Conditions must be observable and deterministic; avoid arbitrary scripting or user-authored code.
- Explainability: battle log records *which directive fired and why*.
- Safeguards: cooldown/resource/range checks, priority starvation prevention, no infinite action loops.
- Optional manual overrides and pause are post-vertical-slice features, not prerequisites for idle play.

## 5. Hero identity and hybrid customization
- Fixed hero identity, element, visuals, signature skill kit, and faction.
- Choose **one of two modest specializations** or a small passive talent package per hero, not an unrestricted classless skill library.
- Weapon mastery adds limited modifiers or passive effects without requiring new art for every combination.
- Keep specializations meaningful but animation-reusable; no unrestricted weapon swapping that breaks sprite silhouettes.
- Experience, level caps, ascension, skill upgrades, and resource costs are data-driven.

## 6. Gear, loot, crafting
- Slots: weapon, armor, accessory, and optionally one additional slot after validation. Avoid early slot inflation.
- Item rarity, main stat, weighted substats, upgrades, set bonuses, and source tables are configurable.
- Provide compare/equip, filtering, auto-salvage, and salvage materials for targeted improvements.
- Salvage guarantees some progress even when random drops disappoint. Avoid unbounded inventory growth.
- Run statistical loot tests before increasing drop-table complexity.

## 7. Summoning
- Earnable in-game currency only, transparent rarity probabilities, guaranteed pity threshold, duplicate compensation.
- No purchases, advertising, energy monetization, or daily coercion.
- Rates, pity, roster weights, and currency economy are data files with deterministic tests.
- Summoning animation should be exciting but skippable.

## 8. Idle and offline systems
- Auto-repeat, stage advance rules, stop conditions (inventory full, repeated losses, target loot), speed settings, and loot summary.
- When a tab is backgrounded or closed, **do not assume combat continues running**. On return, compute capped elapsed-time rewards using a documented deterministic or statistical settlement policy.
- Offline settlement must not fabricate unrestricted progress: account for unlocked stages, team strength, success probability, reward tables, and time caps.
- Keep the visual combat renderer optional for batch tests and offline calculations.
- Protect saves against clock rollback, corrupted payloads, and version changes as reasonably practical for a personal offline game; do not pretend client-only time is tamper-proof.

## 9. UI layouts
### Portrait phone (primary)
Top: compact stage, wave, speed, and pause/auto indicators. Middle **majority of screen**: zoomable isometric battlefield with five allies and enemies readable. Bottom: collapsible five-hero status strip, priority skill/ultimate indicators, rewards/progression tab. Avoid covering battle with permanent debug panels. Large touch targets and adjustable visual scale.

### Desktop / landscape
Center: large isometric arena. Left: compact five-hero frames and buffs. Right: objective, wave, and collapsible encounter/loot info. Bottom: ability and automation indicators, speed and controls. Inventory, summoning, and hero management use separate screens. Desktop has more room but uses the same gameplay rules.

### Screens
Home/stage select; battle; heroes/team; equipment/inventory; directives; progression/upgrades; summon; loot/rewards; settings/save. No account or shop screen.

## 10. Art and animation
- **Detailed 2D pixel art**, original Western grimdark science fantasy; not the low-poly PS2/Valheim look used for Classless Dungeon.
- Isometric or 3/4-view sprites must face and move convincingly across arena directions. Establish direction count and animation frame budget through an early proof-of-concept.
- Large distinctive silhouettes, cohesive pixel scale, readable effects, atmospheric tiled backgrounds, restrained particles on mobile.
- Shared animation state machine (idle, locomotion, attack, cast, hit, down), reusable VFX templates, unique signature effects only where they materially improve identity.
- Placeholder geometry is allowed **during engine prototyping**, but must not be mistaken for final visual approval. A single concept image is not a usable animation sheet.
- Performance tiers: reduce particles/shadows/effects without compromising combat readability or core sprite identity.

## 11. Instrumentation and balance
Headless seeded simulations; automated tests for damage, status resolution, cooldowns, directives, and saves. Track encounter duration, win rate, per-hero DPS, effective healing, damage prevented, buff uptime, debuff uptime, interrupts, cooldown seconds saved, extra attacks enabled, resource contribution, loot per hour, and progression rate. Export CSV/JSON summaries when useful. Compare seeds before and after balance changes.

## 12. Non-goals and decision gates
No multiplayer, open world, complex pathfinding beyond arenas, real-time manual action controls, premium economy, massive initial roster, or external paid services. **Approval required** before adding cloud sync, new recurring costs, a new engine, major camera changes, or expanding scope beyond the current task.
