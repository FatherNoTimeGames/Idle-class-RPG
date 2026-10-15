# Instructions for Codex / coding agents

Read `README.md`, `GAME_DESIGN.md`, `TASKS.md`, and `PROJECT_STATE.md` before work. The repository's current implementation and tests are authoritative for what exists; the design docs describe intended behavior, not completed functionality.

## Strict task execution
1. On **"Continue to the next task"**, locate the **first unchecked task** in `TASKS.md` in document order.
2. Implement **only that one task** and its minimum necessary tests. Do not preemptively start the following task, even if time or tokens remain.
3. If prerequisites are missing or the task would require paid services, broad redesign, or destructive migration, **stop and ask** rather than silently changing scope.
4. Run relevant checks. Mark the task complete **only if its acceptance criteria pass**. If blocked, leave unchecked and document blocker.
5. Update `PROJECT_STATE.md` with completed task, current commit, checks, caveats, and the next unchecked task. Commit task changes where repository access permits; if not, report the exact commands or diff needed. Do not claim a commit/publish occurred unless verified.
6. End with a concise report: task ID, changes, tests/results, playable impact, known limitations, next task ID, estimated complexity (Low/Medium/High). **STOP.**

"Continue" or "continue to the next task" grants one task only. User approval is needed for each subsequent task. Do not combine tasks for efficiency.

## Usage efficiency
- Make targeted edits; avoid refactors not required by the current task.
- Prefer configuration and reusable systems over per-hero hardcoded logic.
- Avoid large generated art batches, huge dependencies, long prose reports, unnecessary repeated searches, and speculative features.
- Use lightweight placeholders until the visual-pipeline task. Do not reduce final visual quality without approval.
- Preserve existing passing tests; add small deterministic tests for new mechanics.
- Keep project state brief enough to resume without re-reading entire chat histories.

## Product boundaries
- Private single-player personal game. Five-hero isometric **2D pixel-art** idle ARPG. No multiplayer, accounts, real-money payments, or paid APIs.
- GitHub is source of truth; ChatGPT Sites is intended preview/deployment target. **Verify Sites compatibility**, never assume automatic import/sync/publishing. Do not create a separate Site or change an existing Site ID without explicit approval.
- Do not touch the Classless Dungeon repository or wiki.
- Do not use third-party game art, proprietary assets, or copied game formulas without permission.
- Never expose secrets in commits. No API keys in client bundles.
- Prioritize Android portrait readability and low-spec performance.
- Never claim background browser execution while a tab is suspended.
