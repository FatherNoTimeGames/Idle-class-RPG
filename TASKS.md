# Ordered Development Tasks

**Rule:** Each user instruction "Continue to the next task" authorizes exactly **one** unchecked `T##` item, then stop. Do not skip ahead. Do not mark complete without meeting acceptance criteria. Each task is a usage checkpoint and should be committed independently where possible.

The sequence below is a planning baseline. A task can be split into smaller tasks **only with user approval**; never silently combine tasks. Complexity is relative, not a token/cost estimate.

## M0 — Architecture and foundation

- [ ] **T00 — Verify Sites workflow and choose stack** (Low)
  - **Done when:** Document verified Sites import/build/publish constraints, renderer recommendation, storage approach, and zero-paid-API path; stop for approval if incompatible.

- [ ] **T01 — Initialize minimal browser project** (Low)
  - **Done when:** Runnable TypeScript app, scripts, lint/typecheck/test setup, README launch instructions; no combat.

- [ ] **T02 — Responsive shell and navigation** (Medium)
  - **Done when:** Portrait and desktop layouts, screen navigation stubs, five-slot party HUD placeholder; test narrow/wide viewports.

- [ ] **T03 — Persistence foundation** (Medium)
  - **Done when:** Versioned local save/load, corruption fallback, schema migration stub, automated round-trip tests.

- [ ] **T04 — Seeded headless simulation skeleton** (Medium)
  - **Done when:** Fixed-timestep clock, seeded RNG, battle state model independent of rendering; repeatability test.

## M1 — First playable five-hero battle

- [ ] **T05 — Arena and entity movement** (Medium)
  - **Done when:** Single isometric arena with simple five-ally/enemy movement, collision spacing, target acquisition; placeholder art.

- [ ] **T06 — Basic attacks and HP** (Medium)
  - **Done when:** Auto-attacks, ranges, HP/damage/death, victory/defeat; tests for deterministic outcomes.

- [ ] **T07 — Five-hero starter data** (Low)
  - **Done when:** Five distinct hero definitions and three enemy archetypes from data; all five appear and act.

- [ ] **T08 — Cooldowns, casts and resources** (Medium)
  - **Done when:** Active skill lifecycle with cooldown/cast/action lock and resource costs; timing tests.

- [ ] **T09 — First complete encounter** (Medium)
  - **Done when:** Wave spawn, end conditions, restart, battle result summary; playable portrait and desktop.

## M2 — Tactical depth and supports

- [ ] **T10 — Stat and damage pipeline** (Medium)
  - **Done when:** Configurable attack/defense/crit/speed formulas with step-by-step testable calculations.

- [ ] **T11 — Elements and status engine** (High)
  - **Done when:** Affinity modifiers, status durations/stacking/cleanse/dispels, tests for edge cases.

- [ ] **T12 — Targeting and positioning behaviors** (Medium)
  - **Done when:** Melee/ranged positioning, enemy targeting preferences, taunt/protect, readable movement.

- [ ] **T13 — Tactical Directives v1** (High)
  - **Done when:** Five ordered rules per hero, conditions/actions, default presets, safe fallback, traceable decisions.

- [ ] **T14 — Non-healing support abilities** (Medium)
  - **Done when:** Oracle tempo and follow-up mechanics; Veilbinder control; tests measure utility not just DPS.

- [ ] **T15 — Counters, assists, empowerment** (High)
  - **Done when:** Reactive counters, coordinated attacks, shared resource, recursion/trigger limits.

- [ ] **T16 — Boss encounter and battle analytics** (Medium)
  - **Done when:** One boss with telegraphs; per-hero DPS, mitigation, uptime, interrupts, support contribution.

## M3 — Visual vertical slice

- [ ] **T17 — Pixel-art visual pipeline proof** (High)
  - **Done when:** One hero and one enemy in true isometric/3-4-view pixel art; movement/attack/cast/hit/down; document asset requirements and frame budget.

- [ ] **T18 — Five-hero animation integration** (High)
  - **Done when:** Integrate readable distinct silhouettes/animations for initial five, using reusable state machines; avoid bulk roster work.

- [ ] **T19 — Combat effects and camera** (Medium)
  - **Done when:** Reusable VFX, floating damage, camera framing/zoom, signature skill presentation, reduced-effects toggle.

- [ ] **T20 — Responsive battle HUD polish** (Medium)
  - **Done when:** Five hero frames, status icons, skill states, speed control, accessibility/readability on phone and desktop.

- [ ] **T21 — Performance checkpoint** (Medium)
  - **Done when:** Measure mobile memory/frame time and provide adjustable quality tiers; document results.

## M4 — Progression and economy

- [ ] **T22 — Hero XP and upgrades** (Medium)
  - **Done when:** Level progression and skill upgrade data, save integration, cap and cost tests.

- [ ] **T23 — Equipment and inventory** (High)
  - **Done when:** Item generation, main/substats, equip/compare, inventory limits; deterministic tests.

- [ ] **T24 — Gear sets and upgrades** (Medium)
  - **Done when:** Set bonuses, enhancement rolls, upgrade costs, probability tests.

- [ ] **T25 — Salvage and targeted crafting** (Medium)
  - **Done when:** Salvage unwanted gear into materials; craft one targeted item category; economy safeguards.

- [ ] **T26 — Hybrid talents and masteries** (High)
  - **Done when:** Two small specializations per initial hero, mastery passives, respec path; balance tests.

## M5 — Idle progression

- [ ] **T27 — Stage selection and progression** (Medium)
  - **Done when:** Multiple stage configs using reused arena framework; unlock and reward rules.

- [ ] **T28 — Auto-repeat and stop conditions** (Medium)
  - **Done when:** Repeat/advance settings, failure thresholds, inventory stop, session summary.

- [ ] **T29 — Offline settlement v1** (High)
  - **Done when:** Elapsed-time capped reward calculation, stage eligibility, success modeling, save safety; no background-tab promise.

- [ ] **T30 — Idle rewards and loot UI** (Medium)
  - **Done when:** Readable earnings summary, equip/salvage quick actions, portrait and desktop views.

- [ ] **T31 — Batch balance harness** (Medium)
  - **Done when:** Headless seeded encounter batches with CSV/JSON output and comparison of two configs.

## M6 — Summoning and content

- [ ] **T32 — Summoning rules** (Medium)
  - **Done when:** Configurable probabilities, pity, duplicate compensation, earnable currency; deterministic tests.

- [ ] **T33 — Summoning presentation** (Medium)
  - **Done when:** Original skippable reveal animation, collection UI, accessible controls.

- [ ] **T34 — Second arena and encounter variety** (Medium)
  - **Done when:** One new environment, new enemy behaviors and boss variation using existing systems.

- [ ] **T35 — Roster expansion gate** (Low)
  - **Done when:** Review animation throughput, balance data, and usage before approving any additional heroes; no automatic bulk generation.

## M7 — Publishing and hardening

- [ ] **T36 — Save recovery and regression suite** (Medium)
  - **Done when:** Migration and corruption tests, simulation invariants, restore/export/import save where feasible.

- [ ] **T37 — Sites integration rehearsal** (Medium)
  - **Done when:** Verify actual import/build/preview on intended Site workflow without altering existing unrelated Sites; document steps.

- [ ] **T38 — Deployment candidate** (Medium)
  - **Done when:** User-approved publish, smoke test portrait/desktop, confirm persistence, report known limitations.

## Completion protocol

After each task: run checks; update the checkbox only if criteria pass; update `PROJECT_STATE.md`; commit if permitted; report exact checks and limitations; identify next task; **stop**. Do not publish without explicit approval.
