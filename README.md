<div align="center">

# 🤖 GlucoVision Assistant Service

**The multimodal AI assistant — voice, vision, and cooking guidance in one conversational interface.**  
*Whisper ASR · LLaMA-3 Vision · TTS · WebSocket streaming · LangChain memory*

[![FastAPI](https://img.shields.io/badge/FastAPI-Python-009688?style=for-the-badge&logo=fastapi)](#)
[![LLaMA](https://img.shields.io/badge/LLaMA--3-Vision-7B3FE4?style=for-the-badge)](#)
[![Whisper](https://img.shields.io/badge/Whisper-ASR-412991?style=for-the-badge)](#)
[![WebSocket](https://img.shields.io/badge/WebSocket-Real--Time-010101?style=for-the-badge)](#)
[![Docker](https://img.shields.io/badge/Docker-Containerised-2496ED?style=for-the-badge&logo=docker)](#)
[![Status](https://img.shields.io/badge/Status-In%20Development-f59e0b?style=for-the-badge)](#)

</div>

---

## 📌 Purpose

GlucoVision Assistant is the **multimodal conversational AI** that patients interact with via voice or camera. A patient can say *"What's in this food?"* while pointing the camera — voice + vision working together seamlessly. It consolidates voice Q&A, vision-based food Q&A, and cooking guidance into one unified assistant experience.

> Three UI modes — voice, camera, text — of **one multimodal experience**, not three separate products.

---

## 📁 Project Structure

```
16-glucovision-assistant-service/
└── (Git repository initialised — structure to be scaffolded)
```

---

## ✨ Planned Features (by phase)

### Phase 1 — Text Chat
- [ ] LLaMA-3 text-based dietary Q&A
- [ ] LangChain conversation memory (10-turn window)
- [ ] Patient health context injection from `07`
- [ ] Safety guardrails (no medication dosage advice)

### Phase 2 — Voice Assistant
- [ ] Whisper ASR: speech → text (faster-whisper CPU optimised)
- [ ] Text-to-Speech response (Coqui TTS / ElevenLabs)
- [ ] WebSocket audio streaming for low-latency voice
- [ ] Multilingual: English + Sinhala approximation

### Phase 3 — Vision & Cooking
- [ ] LLaMA-3 Vision: food photo → safety assessment for diabetics
- [ ] Multimodal fusion: voice + camera → unified LLM prompt
- [ ] Cooking guidance narration from `11` cooking-ai state
- [ ] Session persistence and conversation history

---

## 🚀 Getting Started

### Prerequisites

- Python ≥ 3.11, Ollama (LLaMA-3 Vision), Docker & Docker Compose
- Optional: NVIDIA GPU for faster Whisper + LLM inference

### Setup (once scaffolded)

```bash
pip install -r requirements.txt
uvicorn main:app --reload --port 8011

docker compose up --build
```

---

## 🏗️ Planned Tech Stack

| Layer | Technology |
|---|---|
| Framework | FastAPI (Python) + WebSocket |
| ASR | OpenAI Whisper (faster-whisper / CTranslate2) |
| LLM | LLaMA-3 Vision (Ollama or Together AI) |
| TTS | Coqui TTS (local) / ElevenLabs API |
| LLM Framework | LangChain (conversation memory) |
| Audio Processing | librosa, soundfile, ffmpeg |
| Containerisation | Docker |
| GPU | Optional (faster inference) |

---

## 🔗 Backend Dependencies

| Service | Interaction |
|---|---|
| `15` recommendation-engine | Dietary context for Q&A |
| `11` cooking-ai | Cooking state for guidance narration |
| `07` user-service | Patient health context for personalised responses |
| `05` api-gateway | WebSocket proxying |

---

## 🔐 Security Notes

- Voice recordings not stored — transcribed then immediately discarded
- Vision Q&A images not permanently stored
- LLM safety filter on all outputs — reject medication dosage answers
- System prompt: *"Never advise on insulin dosage, medication changes, or emergency procedures — refer to clinician."*

---

## 🧪 Testing (Planned)

```bash
pytest tests/asr/         # Whisper accuracy on Sri Lankan English
pytest tests/vision/      # LLaMA-3 Vision identifies Sri Lankan food
pytest tests/safety/      # Medication advice prompt → rejected
pytest tests/latency/     # Voice round-trip < 3s
pytest tests/session/     # 10-turn conversation history maintained
```

---

<div align="center">

*Part of the [GlucoVision Platform](../01-glucovision-platform-architecture) — 21-Repo AI Diabetes Management System*

</div>
