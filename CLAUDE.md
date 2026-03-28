# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Project Is

A single-file browser app for British English coaching. Users get daily AI-generated sentences to study, practice speaking them with voice recognition, and receive real-time corrections. No backend, no build step — just `index.html`.

## How to Run

**Locally:** Open `index.html` directly in Chrome (desktop or Android). First launch prompts for API keys.

**Live (GitHub Pages):** `https://sonynavdeep81.github.io/English_App/`
Deploys automatically on every push to `main` via GitHub Actions. No manual deployment needed — just push and the live URL updates within ~1 minute.

## Architecture

**Everything lives in `index.html`** (~3,600 lines). It is self-contained HTML + CSS + JS with no dependencies, no bundler, and no build process.

### Key JS structures

- `callLLM(provider, model, systemPrompt, messages)` — unified abstraction over Gemini, Claude, and OpenAI APIs
- `MODELS` / `PRICING` — config objects for supported providers and per-token cost estimates
- `LEVEL_DESCRIPTIONS` — age-appropriate coaching tone: Young Learner (8–12), Teenager (13–17), Adult (18+)
- LocalStorage keys: `ec_keys` (API keys), `ec_settings` (preferences), `ec_data` (sentences + history)

### LLM providers

| Provider | Default model | Notes |
|----------|--------------|-------|
| Gemini | gemini-2.0-flash | Default; free tier 1,000 req/day |
| Claude | claude-sonnet-4-6 | Higher quality |
| OpenAI | gpt-4o-mini | Alternative |

### Speech

- **STT**: Web Speech API (browser-native, free)
- **TTS**: Azure Neural TTS (`en-GB-RyanNeural` / `en-GB-SoniaNeural`) with browser SpeechSynthesis fallback

### Data flow

1. On load: read `ec_data` from localStorage → render sentence list
2. "Generate" button → `callLLM()` → parse JSON response → save to `ec_data`
3. Voice practice: STT captures spoken text → `callLLM()` with review prompt → parse corrections → render color-coded diff (green = correct, red = mistake, orange = changed word)

## Prompts

The LLM review prompt targets **IELTS Band 8–9** output: full native British corrections (not minimal fixes), British idioms, rich vocabulary. See the `SYSTEM_PROMPT` constant and `english-coach-build-prompt.md` for the full spec.

## Google Sheets Export

Sentence tables are copied as HTML using `google-sheets-html-origin` meta tag so Sheets preserves colors and line breaks on paste. Do not switch to plain-text clipboard formats.
