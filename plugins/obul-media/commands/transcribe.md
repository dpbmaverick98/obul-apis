---
name: transcribe
description: Transcribe audio to text or generate speech from text. Usage: /obul-media:transcribe <file-or-text>
---

Convert between audio and text using x402engine's pay-per-call endpoints.

## Mode Detection

Determine the mode based on the user's input:

- **If the user provides an audio file** (`.mp3`, `.wav`, `.m4a`, `.ogg`, `.flac`, etc.) -> **Transcribe** (speech-to-text)
- **If the user provides text** -> **Text-to-Speech** (generate audio)

## Transcription (Audio to Text)

Use Deepgram Nova-3 for transcription with speaker diarization.

**Cost:** $0.10 per request

```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@recording.mp3" \
  "https://proxy.obul.ai/proxy/https/x402engine.app/api/transcribe"
```

The response includes full text, speaker labels, and timestamps. Display the transcription in a readable format.

## Text-to-Speech (Text to Audio)

Choose the TTS provider based on user preference:

| Provider | Endpoint | Cost | Best For |
|----------|----------|------|----------|
| OpenAI | `/api/tts/openai` | $0.01 | General use, reliable, 6 voices |
| ElevenLabs | `/api/tts/elevenlabs` | $0.02 | Ultra-realistic, multilingual |

**Default to OpenAI** unless the user asks for ElevenLabs or "most realistic" voice.

### OpenAI TTS

```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{"text": "Your text here", "voice": "alloy"}' \
  "https://proxy.obul.ai/proxy/https/x402engine.app/api/tts/openai" \
  -o output.mp3
```

**Available voices:** `alloy`, `echo`, `fable`, `onyx`, `nova`, `shimmer`

### ElevenLabs TTS

```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{"text": "Your text here", "voice": "rachel"}' \
  "https://proxy.obul.ai/proxy/https/x402engine.app/api/tts/elevenlabs" \
  -o output.mp3
```

## Workflow

1. Check that `OBUL_API_KEY` is set
2. Detect mode: transcription (file input) or TTS (text input)
3. Send the request through the Obul proxy
4. For TTS: save the audio file and tell the user where it was saved
5. For transcription: display the text with speaker labels if available
6. Mention the service used and approximate cost
