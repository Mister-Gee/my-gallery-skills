---
name: agent-voice
description: Speaks the AI agent's response aloud using on-device TTS with word-by-word animated highlighting and a live waveform. Use this whenever the user wants to hear spoken replies — it auto-plays immediately. Works fully offline.
metadata:
  homepage: https://mister-gee.github.io/edge-gallery-skills/voice-studio/
---

# Agent Voice

Speaks the AI agent's response aloud with word-by-word animated highlighting and a live waveform visualizer. Powered by the device's built-in TTS engine — fully offline, no API key required.

## Prompts / Triggers
- "Talk to me" / "Speak your responses"
- "Read that aloud"
- "Say [anything]"
- "Tell me [topic]" — respond and speak it
- "I want to hear your answer"
- "Voice mode on"
- "Respond out loud"

## Instructions

After composing your text response, call the `run_js` tool with the following exact parameters to speak it aloud:
- data: A JSON string with the following fields:
  - text: String. The exact text of your response to speak. Required.
  - rate: Number (optional). Speech rate 0.5 (slow) to 2.0 (fast). Defaults to 1.0.
  - pitch: Number (optional). Voice pitch 0.5 (low) to 2.0 (high). Defaults to 1.0.
  - voice: String (optional). Partial voice name to match (e.g. "Google UK English Female").
