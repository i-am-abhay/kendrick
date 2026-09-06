<div align="center">

<img width="1024" height="459" alt="Assistive Communication Translator" src="https://github.com/user-attachments/assets/4e5238bd-5548-4d97-9d20-6e66c1e8b1de" />

### Turning difficult-to-understand speech into clear, natural communication.

</div>

<br><br>

# Assistive Communication Translator

Imagine knowing exactly what you want to say, but having to repeat yourself because a computer cannot understand your speech.

For people with **stuttering, dysarthria, slurring, rapid speech, unusual pronunciation, and other speech differences**, conventional speech recognition can turn an intended sentence into something completely different.

<br>

Assistive Communication Translator is built to change that.

Instead of treating speech recognition as the final step, the system combines **speech-to-text and text-to-speech** with local AI to create a complete communication loop: understand what someone is trying to say, reconstruct the intended message, and give them a clear, natural voice to communicate it.

<br><br>

## An Example

The unusual text below is **deliberately distorted**. It represents an example of how speech might be transcribed when someone is speaking while experiencing difficulty with articulation — such as inconsistent pronunciation, slurring, or rapidly changing speech.

```text
hellllo cann you palsle papwr towoeols plelas
```

Rather than simply accepting that transcription as correct, the system looks at the **entire utterance** and uses context, grammar, phonetic similarity, and relationships between words to determine what the speaker was most likely trying to communicate.

```text
Hello, can you please pass the paper towels?
```

<br>

The goal is not to speak for someone.

**The goal is to help their intended communication be understood — and then give that communication a natural voice.**

<br><br>

## How It Works

```text
Speech
  ↓
Speech-to-Text
  ↓
Local Qwen3 ASR
  ↓
Imperfect transcription
  ↓
Contextual reconstruction
  ↓
Natural English
  ↓
Text-to-Speech
  ↓
Local Qwen3 TTS
  ↓
Spoken communication
```

<br>

**Speech-to-text** is responsible for capturing the speaker's words as accurately as possible, even when the input is difficult, inconsistent, or imperfect.

<br>

**Contextual reconstruction** then looks beyond individual words. The system considers the complete utterance, grammar, meaning, and phonetic relationships to recover the message the speaker is most likely trying to express.

<br>

**Text-to-speech** takes that reconstructed message and turns it back into natural spoken language, allowing the communication to be heard clearly.

<br>

This makes the project more than a speech recognizer.

**It is a communication pipeline from voice → understanding → voice.**

<br><br>

## Built Local-First

The entire communication pipeline is designed to run locally using:

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

<br><br>

## Privacy

Privacy is fundamental to the project.

<br>

Speech can contain incredibly personal information. That's why the core pipeline is designed to run **entirely on your own computer**.

<br>

Your audio, transcriptions, reconstructed messages, and conversations do not need to be sent to a cloud AI service for the system to work.

<br>

**Your voice stays with you. Your words stay with you.**

<br>

Privacy isn't an afterthought.

**It is part of the foundation.**

<br><br>

## Why It Matters

Speech recognition should not assume that everyone speaks in exactly the same way.

A missed syllable, repeated sound, slurred word, or unusual pronunciation should not automatically become a completely different message.

<br>

Assistive Communication Translator explores a more human-centered approach: instead of requiring the speaker to adapt their speech to technology, the technology should become better at adapting to the speaker.

<br>

> **Technology should adapt to the speaker — not require the speaker to adapt to the technology.**

<br>

The long-term goal is a communication tool that makes everyday interactions **easier, more private, and more accessible**, while giving people a better way to both express themselves and be understood.

<br><br>

## Status

**Active development**

<br>

The core local AI pipeline is operational, with ongoing work focused on improving difficult-speech **recognition, contextual reconstruction, microphone reliability, and natural spoken output**.

<br><br>

## License

MIT License
