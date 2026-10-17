# Audio Transcription & Text Annotation Portfolio

## 📌 Project Overview
This repository serves as a professional, no-code portfolio demonstrating my methodology for high-quality **Audio Transcription and Text Labeling**. It simulates enterprise-grade data validation workflows used to train advanced Automatic Speech Recognition (ASR) and conversational AI systems.

This portfolio highlights my capability to apply detailed text normalization rules, manage acoustic environment formatting, and resolve linguistic ambiguity to produce pristine training data.

---

## 🗺️ Framework 1: Audio Transcription Style Guide & Rubric
This framework details the precise guidelines applied when converting raw acoustic data into structured text.

### 1. Orthographic vs. Verbatim Standards
*   **True Verbatim Labeling:** Every sound must be captured exactly as spoken. This includes filler words (`uh`, `um`), false starts (`I went- I ran`), and stutters (`b-b-before`).
*   **Clean Verbatim Labeling:** Filler words, stutters, and accidental repetitions are omitted to focus entirely on the core text content.

### 2. Acoustic Tagging Dictionary
To help speech models understand environmental contexts, specific non-speech events must be meticulously tagged using standard bracket notation:
*   `[laughter]` – Used for audible chuckling or laughing during speech.
*   `[cough]` – Captures throat-clearing, coughing, or sneezing.
*   `[applause]` – Handclapping or crowd cheering.
*   `[unintelligible]` – Applied when audio quality drops and a word cannot be deciphered after 3 consecutive replays.

---

## 📝 Framework 2: Structured Text Dataset Output (JSON Dataset Simulation)
Below is a structured representation of a fully processed, multi-speaker customer service call transcript. It shows how messy, raw audio content is converted into verified, schema-compliant data:

```json
{
  "session_id": "ASR-CALL-LOG-4091",
  "language_code": "en-US",
  "transcription_type": "True_Verbatim",
  "qa_status": "APPROVED",
  "transcript_segments": [
    {
      "segment_id": 1,
      "speaker_label": "Speaker_A_Agent",
      "timestamp_start": "00:00:02.40",
      "timestamp_end": "00:00:06.10",
      "raw_audio_transcript": "Thank you for calling support. Um, [typing] how can I help you today?"
    },
    {
      "segment_id": 2,
      "speaker_label": "Speaker_B_Customer",
      "timestamp_start": "00:00:06.85",
      "timestamp_end": "00:00:11.30",
      "raw_audio_transcript": "Yes, hi. My internet is completely down and [cough] I've tried rebooting it twice."
    },
    {
      "segment_id": 3,
      "speaker_label": "Speaker_A_Agent",
      "timestamp_start": "00:00:11.90",
      "timestamp_end": "00:00:15.50",
      "raw_audio_transcript": "I understand. Let me check the line status on my- [crosstalk] one second."
    }
  ]
}
```

---

## ⚠️ Framework 3: Transcription Edge Case Resolution Log
A primary focus of my work at **OneForma** and **Mindrift** involves identifying data discrepancies and standardizing complex linguistic scenarios:

| Complex Audio Scenario | Immediate Correct Action Protocol | Impact on Speech AI Training |
| :--- | :--- | :--- |
| **Crosstalk / Overlapping Speech** (Two speakers talking simultaneously). | Transcribe the dominant speaker first. Tag overlapping segments with a strict `[crosstalk]` identifier instead of guessing words. | Prevents the acoustic model from learning overlapping phonetic distortions as single words. |
| **Brand Names & Acronyms** (Speaker says "GitHub" or "AI"). | Spell out acronyms exactly as pronounced based on project guidelines (e.g., lowercase vs. uppercase protocols like `A.I.` vs `AI`). | Standardizes vocabulary tokens for downstream text processing. |
| **Background Noise Interference** (A loud siren passes by during a sentence). | Keep transcribing the speech. Insert a continuous `[background_noise]` tag underneath the segment if the voice remains audible. | Teaches the model to isolate human speech from heavy environmental background interference. |
