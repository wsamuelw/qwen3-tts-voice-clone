# Qwen3-TTS Voice Clone

High-quality voice cloning powered by [Qwen3-TTS](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base). Upload a reference audio sample, and this project generates speech that mimics the speaker's voice characteristics — in Chinese or English.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wsamuelw/qwen3-tts-voice-clone/blob/main/qwen3-tts-voice-clone.ipynb)

## Features

- **Zero-shot voice cloning** — no fine-tuning required. A single 10-second reference audio is enough
- **Auto-transcription** — uses Qwen3-ASR to transcribe the reference audio automatically, ensuring accurate speaker embedding alignment
- **Multilingual** — supports Chinese and English speech generation
- **Low resource** — runs on a single T4 GPU in Google Colab (free tier)
- **Fast inference** — generates speech in seconds, not minutes

## How It Works

```
Reference Audio (10s) ──▶ Qwen3-ASR ──▶ ref_text ──┐
                                                    ├──▶ Qwen3-TTS ──▶ Cloned Speech
Text to Speak ──────────────────────────────────────┘
```

The model analyses the timbre, pitch, and prosody of the reference audio, then synthesises new speech that preserves those characteristics while speaking your input text.

## Getting Started

### Google Colab (Recommended)

The fastest way to try it — zero setup required.

1. Click **Open in Colab** above
2. Run all cells
3. Upload a reference audio file when prompted
4. Download your cloned voice


## Use Cases

### Accessibility & Assistive Tech
Restore speech for people who have lost their voice. A short recording before voice loss enables continued communication in their own voice.

### Content Creation
Dub videos, podcasts, and audiobooks without hiring voice actors. Maintain a consistent brand voice across all content.

### Education
Generate language learning materials with natural pronunciation. Create multilingual versions of the same lesson from a single recording.

### Entertainment & Gaming
Bring characters to life with consistent, expressive voices. Localise games into multiple languages while preserving character identity.

### Archival & Preservation
Preserve endangered languages and historical voices. Generate new educational content from archived recordings.

## Impact

Voice cloning technology sits at the intersection of convenience and responsibility. This project demonstrates what's possible with open, reproducible research — and why thoughtful deployment matters.

**What this enables:**
- Creators without big budgets can produce professional voice content
- Language preservation projects can scale without native speakers present for every recording
- Accessibility tools become more natural and personalised

**What to consider:**
- Always obtain consent before cloning someone's voice
- Clearly label AI-generated audio in published content
- Be aware of legal frameworks around synthetic media in your jurisdiction

## Model Details

| Component | Details |
|-----------|---------|
| Model | `Qwen/Qwen3-TTS-12Hz-1.7B-Base` |
| Parameters | 1.7B |
| Sample Rate | 24kHz |
| Languages | Chinese, English |
| Reference Audio | ~10 seconds recommended |
| GPU Memory | ~4GB (bf16) |

Smaller variant also available: `Qwen/Qwen3-TTS-12Hz-0.6B-Base` (fewer parameters, faster inference).

## Project Structure

```
qwen3-tts-voice-clone/
├── qwen3-tts-voice-clone.ipynb   # Full working notebook (recommended starting point)
├── README.md
└── .gitignore
```

## Contributing

Contributions welcome. Open an issue to discuss what you'd like to change, or submit a PR directly.

## License

MIT
