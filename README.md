<div align="center">

<img width="1024" height="459" alt="Assistive Communication Translator" src="https://github.com/user-attachments/assets/4e5238bd-5548-4d97-9d20-6e66c1e8b1de" />

### Turning difficult-to-understand speech into clear, natural communication.

</div>

<br><br>

# Assistive Communication Translator

Imagine knowing exactly what you want to say, but having to repeat yourself because a computer cannot understand your speech.

<br>

For people with **stuttering, dysarthria, slurring, rapid speech, unusual pronunciation, and other speech differences**, conventional speech recognition can turn a simple sentence into something completely different.

<br>

Assistive Communication Translator is built to change that.

<br>

Instead of simply guessing individual words, the system uses **local AI to understand the entire utterance**, considering context, grammar, phonetic similarity, and relationships between words to reconstruct the communication the speaker is most likely trying to express.

<br><br>

For example:

```text
hellllo cann you palsle papwr towoeols plelas
```

becomes:

```text
Hello, can you please pass the paper towels?
```

<br>

The goal is not to speak for someone.

**The goal is to help their actual words be understood.**

<br><br>

## How It Works

```text
Speech
  ↓
Local Qwen3 ASR
  ↓
Imperfect transcription
  ↓
Contextual reconstruction
  ↓
Natural English
  ↓
Local Qwen3 TTS
  ↓
Spoken communication
```

<br>

The system separates speech recognition from language reconstruction so that each stage has a clear purpose.

<br>

**ASR** recovers the spoken content.

<br>

**The language model** interprets the complete utterance and reconstructs the intended message.

<br>

**TTS** gives the speaker a natural spoken output.

<br><br>

## Built Local-First

The core communication pipeline runs locally using:

<br>

| Component                    | Model / Runtime              |
| ---------------------------- | ---------------------------- |
| Speech Recognition           | Qwen3 ASR 1.7B               |
| Communication Reconstruction | Qwen3 4B Instruct            |
| Text-to-Speech               | Qwen3 TTS 0.6B               |
| LLM Runtime                  | llama.cpp                    |
| Acceleration                 | MLX                          |
| Application                  | React + TypeScript + Node.js |

<br>

Local services:

```text
8001  MLX Adapter
8002  Qwen3 LLM
8003  ASR
8004  TTS
3000  Web Application
```

<br>

No Gemini API key is required for the local communication pipeline.

<br><br>

## Why It Matters

Speech recognition should not assume that everyone speaks in exactly the same way.

<br>

A missed syllable, a repeated word, or a slurred sound should not become a completely different message.

<br>

Assistive Communication Translator explores a more human-centered approach:

<br>

> **Technology should adapt to the speaker — not require the speaker to adapt to the technology.**

<br>

The long-term goal is a communication tool that makes everyday interactions easier, more private, and more accessible for people whose speech is often misunderstood by conventional systems.

<br><br>

## Status

**Active development**

<br>

The core local AI pipeline is operational, with ongoing work focused on improving difficult-speech recognition, contextual reconstruction, microphone reliability, and natural spoken output.

<br><br>

## Privacy

Privacy is fundamental to the project.

<br>

The communication pipeline is designed to run **entirely locally on your own computer**. Your speech, transcriptions, and conversations do not need to be sent to a cloud AI service to be processed.

<br>

**Your voice stays with you. Your words stay with you.**

<br>

Privacy isn't an afterthought or an optional feature.

**It is part of the foundation.**

<br><br>

## License

MIT License
