# Mission Control sync

This project is registered in Joey Mission Control as `WOOSONG_3D_CAMPUS` (catalog on the `mc/registry` branch of `JoeyAJ/joey-mission-control`). Follow `AGENT_CONTROL.md` there, section "Sync progress".

After every work session and every version Joey accepts:

1. On `mc/registry`, edit `PROJECTS/WOOSONG_3D_CAMPUS/CURRENT_STATE.md`: yaml `version`, `current_agent`, `agent_model`, `as_of`, the `## Current Stage` text, and add one line at the top of `## Work log`.
2. Update `## Recommended Next Step` in `NEXT_ACTIONS.md` if it changed.
3. Refresh this project's `memoryHashes` in `.mission-control/registration-ledger.json` (SHA-256 of each changed file). Do not edit the receipt, `PROJECT_REGISTRY_V1.0.md` or `MEMORY_INDEX.md`.
4. Validate with `validateRegistrationCatalog` from the latest MC `main`, then fast-forward push. Never force-push.
