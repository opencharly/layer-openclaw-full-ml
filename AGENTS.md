# AGENTS.md — layer-openclaw-full-ml

Standalone candy repo for the `openclaw-full-ml` meta-composition layer — the
OpenClaw full headless stack plus the CUDA speech-ML tools (Whisper STT +
sherpa-onnx TTS). The candy lives in `charly.yml` at the repo root: the composed
`candy:` list and the `plan:` `check:` assertions.

This repo's candy carries **no `skill:` entity**, so this repo projects no
owning skill. The family skill `/charly-openclaw:openclaw-full-ml-layer` (owned
by `opencharly/layer-charly-openclaw`) is the closest procedure, and the gap is
recorded against `opencharly/opencharly#291` (the batch that authors missing
`skill:` entities).

Canonical files:

- `charly.yml` — the `openclaw-full-ml:` candy entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-openclaw:openclaw-full-ml-layer` — the owning skill projected for the
  base OpenClaw full + ML stack (family `openclaw`). Load before editing or
  troubleshooting.
- `/charly-openclaw:openclaw-full` — the base composition this metalayer extends.
- `/charly-tools:whisper` and `/charly-tools:sherpa-onnx` — the speech-ML
  candies composed here.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, the `candy:` composition list, and service
  declarations). Load before editing any entity field or plan step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps assert each composed branch's landed
  artifact (gateway binary, ffmpeg, rg, the whisper script, the sherpa model
  directory) — a no-op composition fails every check.

## Modify this repo

- There is no `skill:` entity to keep in sync; if one is added (per #291), it
  must be edited together with the candy entity in the same change.
- Keep the composed `candy:` list and the per-branch checks in step.
- Pin composed candies at merged tags only.
- New behaviour claims belong in the `plan:` as an observable `check:` step.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
