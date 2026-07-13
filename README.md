# Qwen3-TTS Voice Clone

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wsamuelw/qwen3-tts-voice-clone/blob/main/qwen3-tts-voice-clone.ipynb)
![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![GPU](https://img.shields.io/badge/GPU-T4+-orange.svg)

Voice cloning powered by [Qwen3-TTS](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base). Upload a short reference audio sample, and this project generates speech that mimics the speaker's voice characteristics.

## Use Cases

- **Content creation** — dub videos, podcasts, and audiobooks with a consistent voice
- **Education** — generate language learning materials with natural pronunciation
- **Entertainment** — character voice consistency across games and animations
- **Accessibility** — restore speech for people who have lost their voice (requires prior recording)
- **Archival** — preserve endangered languages and historical voices

## Features

- **Zero-shot voice cloning** — no fine-tuning required. A single 3-second reference audio is enough
- **Auto-transcription** — uses [Qwen3-ASR](https://huggingface.co/Qwen/Qwen3-ASR-0.6B) to transcribe the reference audio automatically, with a chance to confirm or edit before generation
- **Multilingual** — supports 10 languages: Chinese, English, Japanese, Korean, German, French, Russian, Portuguese, Spanish, and Italian. Select from a dropdown or let the notebook auto-detect Chinese/English
- **Low resource** — runs on a single T4 GPU in Google Colab (free tier)
- **Fast inference** — typically under 5 seconds for short text on T4
- **WAV output** — 24kHz sample rate

## How It Works

```
Reference Audio (3-10s) ──▶ Qwen3-ASR ──▶ ref_text ──┐
                                                      ├──▶ Qwen3-TTS ──▶ Cloned Speech
Text to Speak ──▶ Language Detection ─────────────────┘
```

The model analyses the timbre, pitch, and prosody of the reference audio, then synthesises new speech that preserves those characteristics while speaking your input text.

## Getting Started

### Google Colab (Recommended)

The fastest way to try it — zero setup required. First run takes ~3-5 minutes (model download). Subsequent runs are faster.

1. Click **Open in Colab** above
2. Go to **Runtime → Change runtime type** and select **T4 GPU** (if not already selected)
3. Run all cells: **Runtime → Run all** (or press `Ctrl+Shift+F9`)
4. Choose your model, enter the text, and select a language (or leave as Auto)
5. Upload a reference audio file when prompted
6. Wait for the voice clone to generate — it will play and download automatically

### Running Locally

```bash
git clone https://github.com/wsamuelw/qwen3-tts-voice-clone.git
cd qwen3-tts-voice-clone
pip install -r requirements.txt
# Open the notebook in Jupyter:
jupyter notebook qwen3-tts-voice-clone.ipynb
```

**Requirements:** Python 3.10+, NVIDIA GPU with 8GB+ VRAM (CUDA)

## Reference Audio Tips

For best results, your reference audio should be:

- **3–10 seconds** of clear, single-speaker speech
- **No background music**, noise, or reverb
- **Single speaker** — multiple speakers will confuse the model
- **Normal pace** — not too fast, not too slow
- **Clear pronunciation** — mumbling or whispering degrades quality

## Model Details

| Component | Details |
|-----------|---------|
| TTS Model | `Qwen/Qwen3-TTS-12Hz-1.7B-Base` |
| ASR Model | `Qwen/Qwen3-ASR-0.6B` |
| Parameters | 1.7B (TTS), 0.6B (ASR) |
| Sample Rate | 24kHz |
| Output Format | WAV |
| Languages | Chinese, English, Japanese, Korean, German, French, Russian, Portuguese, Spanish, Italian |
| Reference Audio | 3–10 seconds recommended |
| GPU Memory | ~4GB for model weights (bf16); 8-10GB recommended for inference |

Smaller TTS variant also available: `Qwen/Qwen3-TTS-12Hz-0.6B-Base` (faster inference, lower VRAM).

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "No GPU detected" | Go to Runtime → Change runtime type → T4 GPU |
| Voice cloning fails or OOM | Switch to the 0.6B model in the form widget |
| Audio sounds like a different person | Check the transcription shown after upload — edit it if the ASR got any words wrong |
| Audio is garbled or robotic | Upload a cleaner reference audio (3-10s, no background noise) |
| "ASR returned empty transcription" | Upload a file with audible speech, not silence |

## Project Structure

```
qwen3-tts-voice-clone/
├── qwen3-tts-voice-clone.ipynb   # Full working notebook (recommended starting point)
├── requirements.txt              # Python dependencies
├── README.md
├── LICENSE
└── .gitignore
```

## Resources

- [Qwen3-TTS Model Card](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base) — model details, benchmarks, usage policies
- [Qwen3-ASR Model Card](https://huggingface.co/Qwen/Qwen3-ASR-0.6B) — ASR model details
- [qwen-tts PyPI](https://pypi.org/project/qwen-tts/) — Python package
- [qwen-asr PyPI](https://pypi.org/project/qwen-asr/) — Python package

## Contributing

Contributions welcome. Open an issue to discuss what you'd like to change, or submit a PR directly.

## License

This project is licensed under [MIT](LICENSE). The underlying Qwen3-TTS model is licensed under [Apache 2.0](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-Base).

## Ethical Use

This tool is intended for legitimate use cases such as content creation, accessibility, and education.

- **Do not** use this for impersonation, fraud, or deception
- **Always** obtain consent before cloning someone's voice
- **Clearly** label AI-generated audio in published content
- **Be aware** of legal frameworks around synthetic media in your jurisdiction
