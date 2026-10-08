# layer-openclaw-full-ml — RETIRED

This repo is retired. Its only entity was the `openclaw-full-ml` metalayer —
OpenClaw's full headless stack plus the CUDA speech-ML tools (Whisper STT +
sherpa-onnx TTS) — and that variant was **dropped**, not moved, when the OpenClaw
family was consolidated into
[`opencharly/layer-openclaw`](https://github.com/opencharly/layer-openclaw).

The family ships the gateway image and its layer, and nothing else: there is no
`-full`, `-desktop` or `-ml` successor. The composition this layer depended on
(`opencharly/layer-openclaw-full`) is retired in the same cutover, so there is
nothing left for this layer to compose.

Nothing should compose this repo. It is kept only until the operator archives it.
