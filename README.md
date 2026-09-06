<div align="center">
  
<img width="1024" height="459" alt="2df3b00d-7c95-4044-b56b-283bf595d039" src="https://github.com/user-attachments/assets/9b5b14e5-4eb6-44aa-bad1-25d61480a2ee" />

### Turning difficult-to-express thoughts into clear, natural communication.

</div>

<br><br><br>

Imagine knowing exactly what you want to say, but struggling to communicate it clearly.

For some people, the barrier is **speech**. Stuttering, dysarthria, slurring, rapid speech, inconsistent pronunciation, and other speech differences can make conventional speech recognition misunderstand what they are saying.

For others, the barrier is **typing**. Motor difficulties, involuntary keystrokes, repeated or missing letters, inconsistent typing patterns, or difficulty controlling precise movements can make it hard to produce text that accurately reflects what they are trying to communicate.

<br>

The thought is still there.

**The communication system just needs to be better at understanding it.**

<br>

That is what motivated me to build **Assistive Communication Translator**.

I wanted to explore a system that does not force someone to repeatedly correct themselves or change the way they communicate simply because a computer expects perfectly clean input.

Instead, the technology should adapt to the person.

Whether the input comes from **speech or typing**, the goal is the same:

**understand the intended message and help express it naturally.**

<br><br>

## An Example

The unusual text below is **deliberately distorted**. It represents an example of imperfect input, such as what a speech-recognition system might produce when speech contains inconsistent articulation, repeated sounds, slurring, or other difficulties.

It can also represent the kinds of imperfect text that may occur when someone has difficulty producing accurate keystrokes.

```text
hellllo cann you palsle papwr towoeols plelas
```

Rather than treating each unusual word as an isolated spelling error, the system looks at the **complete utterance** and considers context, grammar, phonetic similarity, word relationships, and overall meaning.

```text
Hello, can you please pass the paper towels?
```

<br>

The goal is not to speak for someone.

**The goal is to help their intended communication be understood.**

<br><br>

## How It Works

Assistive Communication Translator is built around a two-way communication pipeline that connects **speech, text, understanding, and spoken output**.

```text
                         INPUT
                           │
                ┌──────────┴──────────┐
                │                     │
             Speech                 Typing
                │                     │
                ▼                     │
         Speech-to-Text               │
                │                     │
         Local Qwen3 ASR              │
                │                     │
                └──────────┬──────────┘
                           ▼
                Imperfect Input
                           │
                           ▼
            Contextual Reconstruction
                           │
                           ▼
                  Intended Message
                           │
                           ▼
                 Clear Natural Text
                           │
                           ▼
                   Text-to-Speech
                           │
                    Local Qwen3 TTS
                           │
                           ▼
                  Spoken Communication
```

<br>

### Speech-to-Text

The speech pathway begins with **speech-to-text**.

Spoken input is processed using **Qwen3 ASR**, converting the user's voice into text.

The system is designed with the understanding that speech may not always be perfectly articulated. A transcription can contain repeated letters, missing sounds, incorrect words, or other errors and still contain enough information to recover the speaker's intended message.

<br>

### Typing Assistance

Communication difficulties are not limited to speech.

Someone may know exactly what they want to write while having difficulty producing accurate text because of **motor impairments, involuntary keystrokes, repeated letters, missing letters, inconsistent typing, or difficulty with precise keyboard control**.

Instead of requiring perfect text input, the system can treat imperfect typing as another form of noisy communication and use the surrounding context to help reconstruct the intended message.

<br>

### Contextual Reconstruction

This is where the system goes beyond ordinary spell-checking.

The local language model considers the **entire message**, rather than correcting words independently.

It can use:

* Context
* Grammar
* Sentence structure
* Phonetic similarity
* Relationships between words
* Natural language patterns
* Overall semantic coherence

The goal is to identify the interpretation that best fits the complete message while avoiding unnecessary changes.

<br>

### Text-to-Speech

Once the intended message has been reconstructed, **text-to-speech** turns it back into spoken communication using **Qwen3 TTS**.

This matters because communication should not stop at generating correct text.

For someone who has difficulty producing speech, the final step can provide a **natural spoken voice** for the message they were trying to express.

<br>

That creates a complete communication loop:

**Speech or Typing → Understanding → Clear Text → Natural Speech**

The project therefore combines **speech-to-text and text-to-speech** rather than treating them as separate technologies.

<br><br>

## Built Local-First

Privacy is fundamental to this project.

Speech and text can contain deeply personal information. Conversations may include names, addresses, private thoughts, medical information, or anything else a person may not want transmitted to a third-party service.

That is why the core communication pipeline is designed to run **entirely on the user's own computer**.

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

Your audio and text can be processed directly on your device rather than being sent to a cloud AI provider simply to be understood.

**Your voice stays with you. Your words stay with you.**

<br>

Privacy is not an optional feature added after the fact.

**Privacy is part of the foundation.**

<br><br>

## Why It Matters

Most speech and language technology is built around the assumption that input will be relatively clean and consistent.

Real people do not always have that ability.

A repeated sound should not automatically become a different word.

A missed letter should not erase someone's intended meaning.

A slurred word should not automatically be interpreted as something unrelated.

And someone should not have to repeatedly correct themselves just to communicate something they already know.

<br>

Assistive Communication Translator explores a more human-centered approach:

> **Technology should adapt to the person — not require the person to adapt to the technology.**

<br>

The project is ultimately about reducing the gap between **what someone wants to communicate** and **what technology is capable of understanding**.

<br><br>

## The Bigger Idea

At its core, this project is not simply a spell checker.

It is not simply speech recognition.

It is not simply text-to-speech.

It is not even simply an AI writing assistant.

It is an exploration of what happens when technology treats **imperfect input as meaningful communication rather than meaningless errors**.

<br>

Someone can have a perfectly clear thought even when their speech or typing does not come out perfectly.

The challenge is building technology capable of recognizing that difference.

<br>

**Imperfect input does not mean imperfect thoughts.**

<br>

*kendrick* is an attempt to bridge that gap.

<br><br>

## Privacy by Design

The local-first architecture is intentional.

The system is designed so that the core processing stages can communicate with one another directly on the user's machine:

```text
Microphone / Keyboard
        ↓
Local Application
        ↓
Local AI Services
        ↓
Local Reconstruction
        ↓
Local Speech Output
```

No cloud communication service is required for the core pipeline.

This approach provides a foundation for greater privacy and gives users more control over where their communication data is processed.

<br><br>

## Accessibility

This project is intended to explore assistive technology for people who experience difficulties with:

* Speech production
* Speech recognition
* Typing
* Written communication
* Precise keyboard control
* Consistent articulation
* Producing clear spoken output

The project does not assume that one communication method works for everyone.

The goal is to provide another way for people to communicate when conventional interfaces create unnecessary barriers.

<br><br>

## Status

**Active development**

The core local AI pipeline is operational, with ongoing work focused on improving:

* Difficult-speech recognition
* Contextual reconstruction
* Typing correction
* Microphone reliability
* Natural spoken output
* Overall accessibility and usability

The project is still experimental, and continued development is focused on making the system more reliable in real-world communication scenarios.

<br><br>

## Disclaimer

Assistive Communication Translator is an **open-source experimental project**.

It is **not a medical device, diagnostic tool, or substitute for professional medical care, speech-language pathology, or other professional assistance**.

The system is intended to assist with communication, but it cannot guarantee that every transcription, reconstruction, or generated voice output will be correct.

AI models can misunderstand speech, typing, context, names, terminology, or user intent and may produce unintended results.

For important, sensitive, or safety-critical communication, users should verify the generated message before relying on it.

<br><br>

## AI Limitations

The underlying models may:

* Misinterpret unclear or distorted speech
* Change the meaning of an input while attempting to correct it
* Remove words that were intentionally repeated
* Introduce words that were not intended
* Struggle with unfamiliar names or terminology
* Misinterpret unusual typing patterns
* Produce a natural-sounding voice that does not accurately reflect the intended message

For this reason, generated output should be treated as a **best-effort interpretation**, not as a guaranteed representation of what the user intended.

<br><br>

## Privacy Note

The core pipeline is designed to run locally, but **local processing does not automatically guarantee complete privacy**.

Privacy can also depend on the operating system, browser, installed software, backups, logs, network configuration, and other applications running on the device.

Users should run the project on devices they trust and review their own system configuration when privacy is especially important.

<br><br>

## Intended Use

This project is intended for **education, experimentation, accessibility research, and assistive communication development**.

It should not be treated as a clinically validated communication system.

The project is an exploration of how local AI can help reduce communication barriers while keeping sensitive information under the user's control.

<br><br>

## Contributions

Contributions, ideas, testing, accessibility feedback, and improvements are welcome.

Because this project focuses on communication accessibility, feedback from people with lived experience of speech or typing impairments can be especially valuable.

<br><br>

## License

MIT License
