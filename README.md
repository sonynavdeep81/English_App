# British English Coach — My Setup

## Models Currently in Use

| Purpose | Service | Model | Cost |
|---------|---------|-------|------|
| Daily sentences (text generation) | OpenAI | GPT-4o Mini | ~₹2/hr |
| Conversation (AI responses) | OpenAI | GPT-4o Mini | ~₹2/hr |
| AI voice (text-to-speech) | Azure TTS | en-GB-RyanNeural / en-GB-SoniaNeural | Free tier |
| My voice (speech-to-text) | Web Speech API (Chrome built-in) | — | Free |

## Available STT Options (if I want to upgrade)

| Engine | Quality | Cost |
|--------|---------|------|
| Web Speech API | Basic | Free |
| Azure Speech | Better | ~₹20/hr |
| OpenAI Whisper | Best | ~₹30/hr |

> To switch STT: Settings → Speech-to-Text → select engine

### Setting up Azure STT (when needed)

Azure STT uses the same key as Azure TTS, but the Azure resource must have **Speech Services** enabled (not just TTS).

1. Go to [portal.azure.com](https://portal.azure.com)
2. Create a resource → search **"Speech"** → select **Speech Services**
3. Choose free tier (F0) — includes both STT and TTS
4. Once created, go to the resource → **Keys and Endpoint** → copy Key 1
5. In the app: Settings → Azure TTS Key → paste the key, set region to match your resource (e.g. `centralindia`)
6. Settings → Speech-to-Text → select **Azure Speech**

## Azure TTS (Text-to-Speech)

Currently using **en-GB-RyanNeural** (Oliver, male) and **en-GB-SoniaNeural** (Emma, female) — Azure's highest quality Neural British English voices.

### Free Tier Limits

- **500,000 characters/month** free
- At current usage (~11 sessions/day, ~3,000 chars/session) = ~33,000 chars/day = well within limit
- Resets on the 1st of every month

### If Free Quota Runs Out Early

When the free quota is exhausted, TTS will stop working and the app will fall back to the browser's built-in robotic voice.

**Option 1 — Wait for monthly reset** (free, no action needed)

**Option 2 — Enable pay-as-you-go on Azure**
1. Go to [portal.azure.com](https://portal.azure.com)
2. Upgrade your subscription to pay-as-you-go (add credit card)
3. TTS will continue working automatically — no app changes needed
4. Cost after free tier: **$16 per 1 million characters** (~₹1,336) — at normal usage roughly ₹50–100/month extra

**Option 3 — Switch to OpenAI TTS** (higher cost, slightly better quality)
- Settings → (future option if added) — costs ~₹125/hr

## Available LLM Options

| Provider | Model | Cost |
|----------|-------|------|
| Google Gemini | gemini-2.0-flash | Free (1,000 req/day) |
| OpenAI | GPT-4o Mini | ~₹2/hr |
| OpenAI | GPT-4o | Higher quality, higher cost |
| Anthropic | Claude Sonnet | Higher quality, higher cost |

## Live App

`https://sonynavdeep81.github.io/English_App/`

## Notes

- All API keys are stored locally in the browser (localStorage) — never sent anywhere except the respective API provider.
- Azure TTS free tier has a monthly limit of 500,000 characters. Sufficient for regular daily use.
- Costs shown are estimates based on ₹83.5 per USD.
