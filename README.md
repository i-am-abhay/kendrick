<div align="center">

<img width="1024" height="459" alt="Assistive Communication Translator" src="https://github.com/user-attachments/assets/4e5238bd-5548-4d97-9d20-6e66c1e8b1de" />

### Turning difficult-to-express thoughts into clear, natural communication.

</div>

<br><br>

# Assistive Communication Translator

Imagine knowing exactly what you want to say, but struggling to communicate it clearly.

For some people, the barrier is **speech**. Stuttering, dysarthria, slurring, rapid speech, inconsistent pronunciation, and other speech differences can make conventional speech recognition misunderstand what they are saying.

For others, the barrier is **typing**. Involuntary keystrokes, repeated or missing letters, motor difficulties, inconsistent typing patterns, or simply being unable to type accurately can turn a simple sentence into something that no longer reflects what they actually meant.

<br>

The thought is still there.

**The communication system just needs to be better at understanding it.**

<br>

That is what motivated me to build **Assistive Communication Translator**.

Instead of requiring someone to repeatedly correct themselves or force their communication into a format that technology understands, the system is designed to work with imperfect input.

Whether that input comes from **speech or typing**, the goal is the same: understand the message behind the input and help express it naturally.

<br><br>

## An Example

The distorted text below is **intentional**. It represents an example of imperfect input — similar to what can happen when speech is difficult to articulate or when someone has difficulty producing accurate text.

```text
hellllo cann you palsle papwr towoeols plelas
```

Rather than treating every unusual word as an isolated error, the system considers the **entire message**, using context, grammar, phonetic similarity, word relationships, and overall meaning to reconstruct what the person was most likely trying to communicate.

```text
Hello, can you please pass the paper towels?
```

<br>

The goal is not to replace someone's voice or thoughts.

**The goal is to help their intended communication come through clearly.**

<br><br>

## How It Works

Assistive Communication Translator is designed around a two-way communication pipeline.

```text
                 INPUT
                   │
          ┌────────┴────────┐
          │                 │
       Speech             Typing
          │                 │
          ▼                 ▼
   Speech-to-Text      Text Input
          │                 │
          └────────┬────────┘
                   ▼
        Contextual Reconstruction
                   │
                   ▼
          Intended Message
                   │
                   ▼
          Text-to-Speech
                   │
                   ▼
        Natural Spoken Output
```

<br>

### Speech-to-Text

The speech pathway begins with **local speech recognition**.

The system converts spoken input into text using **Qwen3 ASR**, including speech that may contain repetitions, slurring, inconsistent pronunciation, rapid delivery, or other difficulties.

The resulting transcription does not have to be perfect.

It becomes the raw material for the next stage.

<br>

### Typing Assistance

Communication difficulties aren't limited to speech.

Someone may know exactly what they want to write but struggle to produce accurate text because of **motor difficulties, involuntary keystrokes, repeated letters, missing letters, inconsistent typing, or other typing impairments**.

The same contextual reconstruction approach can be applied to this imperfect text, helping recover the intended message instead of forcing the user to repeatedly retype it.

<br>

### Contextual Reconstruction

This is where the system goes beyond traditional word-by-word correction.

The local language model considers the **complete utterance**, including grammar, surrounding words, relationships between concepts, likely phrasing, and the meaning of the sentence.

The objective is to recover the message that makes the most sense while avoiding unnecessary changes to what the user actually intended.

<br>

### Text-to-Speech

Once the intended message has been reconstructed, **Qwen3 TTS** converts it into natural spoken language.

This creates a complete communication loop:

**Input → Understanding → Clear Text → Natural Speech**

The result can give someone another way to communicate when producing speech or typing accurately is difficult.

<br><br>

## Built Local-First

Privacy is fundamental to this project.

Speech and text can contain deeply personal information. Conversations may include names, addresses, private thoughts, medical information, or anything else a person would not want uploaded to a third-party service.

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

Your speech and text do not need to leave your device simply to be understood.

**Your voice stays with you. Your words stay with you.**

<br>

Privacy is not an extra feature added to the project.

**Privacy is part of the foundation.**

<br><br>

## Why It Matters

Communication technology often assumes that people will provide **clean, consistent input**.

Real people don't always have that ability.

A repeated syllable should not become a completely different sentence.

A missed letter should not erase someone's intended meaning.

A slurred word should not automatically be treated as an unrelated word.

And someone should not have to repeatedly correct themselves just to communicate something they already know how to say.

<br>

Assistive Communication Translator explores a more human-centered approach:

> **Technology should adapt to the person — not require the person to adapt to the technology.**

<br>

The long-term goal is to make everyday communication **easier, more private, and more accessible** for people whose speech or typing can be difficult for conventional systems to interpret.

<br><br>

## The Bigger Idea

At its core, this project is not really about fixing spelling.

It is not simply about speech recognition.

And it is not simply about text-to-speech.

It is about recognizing that **imperfect input does not mean imperfect thoughts**.

Someone can know exactly what they want to communicate even when their speech or typing does not come out the way they intended.

Assistive Communication Translator is an attempt to bridge that gap.

<br>

**From difficult input to understandable communication.**

<br><br>

## Status

**Active development**

The core local AI pipeline is operational, with ongoing work focused on improving difficult-speech recognition, typing reconstruction, contextual understanding, microphone reliability, and natural spoken output.

<br><br>

## License

MIT License
