# CLAUDE.md

## What this repository is

Desired-state deployment for one ONCE server on Google Cloud. `colors.yml` is
source; `.colors/` is generated and must never be edited or committed. The desired backend is now R2 with compute-require-existing-state enabled.
The former local state must be retained until an explicit ownership transfer
is complete. See compute-migration.md before any real operation.

The root `green`, `red`, and `blue` launchers are copies of the corresponding
packages under `.agents/skills/`, installed from `getcolors/once` and recorded
in `skills-lock.json`. After `npx skills update -p -y`, synchronize all three
root launcher copies.

## Commands

```sh
./green build
./green create --dry-run
./green create
./green delete
```

Build and dry-run require no credentials. Real provider operations use Application Default Credentials plus `COLORS_PAR_*` secrets loaded from the ignored
`.envrc.private`. Never export `COLORS_PAR_PROFILE`.

Keep `compute-prevent-destroy: true`. Lift it only for one authorized delete
with `COLORS_PAR_COMPUTE_PREVENT_DESTROY=false`; never run a real create or
delete without explicit authorization.

## Git

Do not commit or push unless explicitly asked.
