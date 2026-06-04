# Multilingual Voice Pipeline

> End-to-end speech-to-speech translation pipeline: **English Audio → Transcription → Turkish Translation → Turkish Speech**

[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)](https://pytorch.org/)
[![GPU](https://img.shields.io/badge/GPU-CUDA-76b900.svg)](https://developer.nvidia.com/cuda-toolkit)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

---

## 🎯 Overview

This project combines three state-of-the-art models into a single voice pipeline that takes English speech as input and produces Turkish speech as output — with the original speaker's voice preserved via voice cloning.

**Pipeline flow:**

```
🎙️  English Audio (.flac/.wav)
        │
        ▼
┌───────────────────────┐
│  Whisper (large-v3)   │  ← Automatic Speech Recognition
└───────────────────────┘
        │  English text
        ▼
┌───────────────────────┐
│  Qwen2.5-1.5B-Instruct│  ← LLM-based Translation
└───────────────────────┘
        │  Turkish text
        ▼
┌───────────────────────┐
│  Coqui XTTS-v2        │  ← Voice-cloned TTS
└───────────────────────┘
        │
        ▼
🔊 Turkish Audio (cloned voice)
```

## 🛠️ Tech Stack

| Component | Model | Purpose |
|-----------|-------|---------|
| ASR | OpenAI Whisper large-v3 | Speech → Text |
| LLM | Qwen2.5-1.5B-Instruct | Translation (EN → TR) |
| TTS | Coqui XTTS-v2 | Text → Speech (multilingual + voice cloning) |
| Framework | 🤗 Transformers, PyTorch | Model loading & inference |
| Dataset (eval) | PolyAI/minds14 | Benchmark audio samples |

## 💻 Hardware Requirements

Tested on:
- **GPU:** NVIDIA RTX 5000 Ada (32 GB VRAM)
- **CUDA:** 12.x
- **RAM:** 32 GB+
- **OS:** Ubuntu 22.04 / Windows 11

Minimum recommended: 16 GB VRAM (with model quantization).

## 🎧 Demo

> Audio samples are in [`/demo`](./demo). Listen to the input/output side by side.

| Input (EN) | Output (TR) |
|------------|-------------|
| `demo/sample_en.flac` | `demo/sample_tr.wav` |

<!-- Bir YouTube/Loom demo linki eklemek istersen:
[📺 Watch full demo](https://youtu.be/...)
-->

## 📊 Benchmarks

| Stage | Model size | Avg. latency (RTX 5000) |
|-------|-----------|-------------------------|
| ASR (Whisper large-v3) | ~3 GB | ~1.2 s / 10s audio |
| Translation (Qwen 1.5B) | ~3 GB | ~0.8 s / sentence |
| TTS (XTTS-v2) | ~2 GB | ~2.5 s / sentence |
| **End-to-end** | ~8 GB VRAM | **~4–5 s / utterance** |

## 🔒 Source Code

The source code (notebooks, prompt engineering, fine-tuning scripts) is kept in a **private repository**.

If you would like to:
- 🤝 Collaborate or contribute
- 🔍 Review the implementation
- 💼 Discuss potential applications

→ Please reach out via [LinkedIn](https://linkedin.com/in/your-handle) or [email](mailto:you@example.com).

## 🗺️ Roadmap

- [x] EN → TR speech-to-speech pipeline
- [x] Voice cloning with reference audio
- [ ] Real-time streaming mode
- [ ] Additional language pairs (DE, ES, FR)
- [ ] Web UI (Gradio / Streamlit)
- [ ] Latency optimization with TensorRT / ONNX

## 📚 References

- [Whisper (OpenAI)](https://github.com/openai/whisper)
- [Qwen 2.5 (Alibaba)](https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct)
- [Coqui XTTS-v2](https://huggingface.co/coqui/XTTS-v2)
- [PolyAI minds14 Dataset](https://huggingface.co/datasets/PolyAI/minds14)

## 📄 License

This documentation is licensed under the MIT License — see [LICENSE](./LICENSE) for details.
The source code itself is proprietary and not publicly distributed.

## 👤 Author

**[Your Name]** — *AI / Speech Engineer*
🔗 [GitHub](https://github.com/your-handle) · [LinkedIn](https://linkedin.com/in/your-handle)
