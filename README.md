# openclaw-full-ml

The OpenClaw full headless stack plus CUDA speech-ML tools, as a charly
*meta-composition* layer.

The `openclaw-full-ml` candy installs nothing of its own; it composes three
candies, so the observable effect is the union of their key artifacts:

- `openclaw-full` — the OpenClaw gateway plus every headless CLI tool (ffmpeg,
  ripgrep, gh, tmux, sqlite, uv, …). The gateway binary lands at
  `~/.npm-global/bin/openclaw` and `ffmpeg`/`rg` at `/usr/bin`.
- `whisper` — OpenAI Whisper speech-to-text installed via pixi into the shared
  default environment, exposing the `whisper` console script at
  `~/.pixi/envs/default/bin/whisper` (ffmpeg is its audio decoder).
- `sherpa-onnx` — offline text-to-speech whose VITS piper voice model is
  downloaded to
  `~/.local/share/sherpa-onnx/models/vits-piper-en_US-lessac-high`.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `openclaw-full-ml` |
| Type | Meta-composition — installs nothing of its own |
| Composes | `layer-openclaw-full`, `layer-whisper`, `layer-sherpa-onnx` |
| STT | `~/.pixi/envs/default/bin/whisper` |
| TTS | `~/.local/share/sherpa-onnx/models/vits-piper-en_US-lessac-high` |
| Service / port | none of its own |

## How to use it

Compose the metalayer inside a box body (the box name's `candy:` node is the box body, whose keys are `base:` and a `candy:` list):

```yaml
openclaw-full-ml:
  candy:
    base: cachyos
    candy:
      - '@github.com/opencharly/layer-openclaw-full-ml:v2026.239.1611'
```

Each branch is verifiable by the presence of its landed artifact, so a no-op
composition fails every check.

## Layout

- `charly.yml` — the `openclaw-full-ml:` candy entity (the composed `candy:`
  list and the `plan:` `check:` assertions).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

This repo carries no `skill:` entity of its own; `/charly-openclaw:openclaw-full-ml-layer` is the closest
family owning procedure.

- Base composition: `/charly-openclaw:openclaw-full`.
- STT: `/charly-tools:whisper`. TTS: `/charly-tools:sherpa-onnx`.
- [`opencharly/opencharly](https://github.com/opencharly/opencharly) — the umbrella.
