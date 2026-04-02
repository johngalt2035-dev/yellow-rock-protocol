# LLM Provider Setup Guides

Yellow Rock works with any large language model. Choose your provider:

## OpenAI (ChatGPT)

1. Go to [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. Create a new API key
3. Set environment variable: `export OPENAI_API_KEY=sk-...`
4. In config: `"provider": "openai", "model": "gpt-4o"`

**Recommended models**: `gpt-4o` (best quality), `gpt-4o-mini` (budget)

## Anthropic (Claude)

1. Go to [console.anthropic.com](https://console.anthropic.com/)
2. Create an API key under Settings
3. Set environment variable: `export ANTHROPIC_API_KEY=sk-ant-...`
4. In config: `"provider": "claude", "model": "claude-sonnet-4-20250514"`

**Recommended models**: `claude-sonnet-4-20250514` (best balance), `claude-opus-4-20250514` (highest quality)

## xAI (Grok)

1. Go to [console.x.ai](https://console.x.ai/)
2. Create an API key
3. Set environment variable: `export XAI_API_KEY=xai-...`
4. In config: `"provider": "xai", "model": "grok-4-1-fast-reasoning"`

**Recommended models**: `grok-4-1-fast-reasoning` (best quality), `grok-4-1-fast-non-reasoning` (budget)

## Google (Gemini)

1. Go to [aistudio.google.com](https://aistudio.google.com/)
2. Get an API key
3. Set environment variable: `export GOOGLE_API_KEY=...`
4. In config: `"provider": "gemini", "model": "gemini-2.5-pro"`

**Recommended models**: `gemini-2.5-pro` (best quality), `gemini-2.0-flash` (budget/free)

## Ollama (Local / Free)

1. Install from [ollama.com](https://ollama.com/)
2. Pull a model: `ollama pull llama3.2:8b`
3. No API key needed (runs locally)
4. In config: `"provider": "ollama", "model": "llama3.2:8b"`

**Recommended models**: `llama3.2:8b` (best local quality), `llama3.2:3b` (lighter)

## Provider Comparison

| Provider | Quality | Speed | Cost | Privacy | Offline |
|----------|---------|-------|------|---------|---------|
| OpenAI | Excellent | Fast | $$$ | Cloud | No |
| Claude | Excellent | Fast | $$$ | Cloud | No |
| xAI Grok | Very Good | Very Fast | $$ | Cloud | No |
| Gemini | Good | Fast | Free-$$ | Cloud | No |
| Ollama | Good | Medium | Free | Local | Yes |

## System Prompt

Regardless of provider, copy the contents of `templates/generic/system-prompt.md` into your AI's system prompt. All providers use the same protocol.
