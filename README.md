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
