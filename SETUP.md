# Getting Started with Grey Rock

Set up your Executive Assistant utilizing the Grey Rock communications protocol in 5 minutes. No technical background required.

---

## Step 1: Choose Your AI Assistant (2 minutes)

Grey Rock works with any AI. Pick one and get an API key:

| Provider | Best For | Cost | Get API Key |
|----------|----------|------|-------------|
| **OpenAI (ChatGPT)** | Most popular, reliable | ~$0.01/message | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) |
| **Anthropic (Claude)** | Excellent instruction following | ~$0.01/message | [console.anthropic.com](https://console.anthropic.com/) |
| **xAI (Grok)** | Fast, reasoning capable | ~$0.005/message | [console.x.ai](https://console.x.ai/) |
| **Google (Gemini)** | Good free tier | Free tier available | [aistudio.google.com](https://aistudio.google.com/) |
| **Ollama (Local)** | Free, runs on your computer | Free | [ollama.com](https://ollama.com/) |

Save your API key somewhere safe. You'll need it in Step 3.

## Step 2: Choose Your Messaging Platform

| Platform | Setup Difficulty | Best For |
|----------|-----------------|----------|
| **Signal** | Medium | Privacy-focused, encrypted |
| **Telegram** | Easy | Quick bot setup, groups |
| **WhatsApp** | Hard | Most widely used globally |
| **SMS** | Medium | Via Twilio, AWS SNS, or VoIP.ms |

See the platform-specific guides in `templates/channels/` for detailed setup instructions.

## Step 3: Configure Your Contacts (3 minutes)

Open the file `grey-rock-config.json` in any text editor and fill in:

### Your Info
```json
"user": {
  "name": "Your First Name",
  "timezone": "America/New_York"
}
```

### Your Contacts

For each high-conflict counterparty, add an entry:
```json
{
  "id": "opposing-counsel",
  "name": "Their Name",
  "phone": "+15551234567",
  "channels": ["signal", "sms"],
  "primary_channel": "signal",
  "protocol": "grey-rock",
  "communication_style": "executive"
}
```

For normal contacts (trusted colleagues, professional contacts you work well with):
```json
{
  "id": "trusted-colleague",
  "name": "Colleague Name",
  "phone": "+15559876543",
  "channels": ["signal"],
  "primary_channel": "signal",
  "protocol": "normal",
  "communication_style": "personal"
}
```

### YAML Format (simpler — no brackets or commas needed)

Save as `contacts.yaml`:
```yaml
contacts:
  - id: opposing-counsel
    name: Contact A
    channels: [signal, sms]
    primary_channel: signal
    protocol: grey-rock
    communication_style: executive

  - id: trusted-colleague
    name: Contact B
    channels: [signal]
    primary_channel: signal
    protocol: normal
    communication_style: personal
```

Both JSON and YAML formats are accepted. YAML is easier for humans — no brackets, no commas, no quotes needed for most values.

## Step 3b: Choose Communication Style

Each contact can have its own communication style:

| Style | When to Use | Example |
|-------|-------------|---------|
| **Executive** | Litigation, formal disputes, regulatory matters | "I will review that matter and respond accordingly." |
| **Personal** | Trusted contacts, casual business relationships | "Got it, I'll check on that." |

Set `"communication_style"` per contact. The global default is configured in `communication_style.default` in your config file.

### Your AI Choice
```json
"llm": {
  "provider": "openai",
  "model": "gpt-4o",
  "api_key_env": "OPENAI_API_KEY"
}
```

### Your Schedule
```json
"message_window": {
  "active_start": "07:00",
  "active_end": "22:00",
  "timezone": "America/New_York"
}
```

Messages are only sent during this window. Outside these hours, the system is silent.

## Step 4: Install Grey Rock Memory (5-20 minutes)

Follow the installation guide for your platform: **[INSTALL.md](INSTALL.md)**
- [macOS](#macos) | [Windows](#windows) | [Ubuntu](#ubuntu--debian) | [Fedora](#fedora--rhel--centos)

Or let your AI do it: **[AI-INSTALL.md](AI-INSTALL.md)**

Once installed, start the memory system:
```bash
# Mac / Linux:
grey-rock-memory --db ~/.grey-rock/memory.db serve --port 9077

# Windows (PowerShell):
grey-rock-memory --db "$env:USERPROFILE\.grey-rock\memory.db" serve --port 9077
```

### Train with background knowledge (optional)

Create a file `background.json` with facts the system should know:
```json
[
  { "title": "Meeting schedule", "content": "Weekly sync Mondays at 10am. Board meeting first Thursday of month." },
  { "title": "Key deadlines", "content": "Q2 deliverables due June 30. Contract renewal August 15." }
]
```

Then import:
```bash
grey-rock-memory --db ~/.grey-rock/memory.db train background.json
```

## Step 5: Test It

Send a test message and verify the system responds appropriately:

- **Grey rock contacts**: Should get brief, neutral, factual responses
- **Normal contacts**: Should get natural, friendly responses
- **During silent window**: No responses until the active window opens

## Easiest Method: Configure via Chat

If you're using OpenClaw, you can add contacts and training data by simply messaging your assistant via Signal, WhatsApp, Telegram, or SMS:

**Add a contact:**
> "Add opposing-counsel as a grey-rock executive contact on Signal: +15551234567"

**Add training data:**
> "Remember: Contact A works Mon-Fri 9-5. Standing meetings are Tuesdays at 3pm."

**Change a contact's style:**
> "Switch opposing-counsel to personal communication style"

**Check current contacts:**
> "List all my grey-rock contacts"

OpenClaw will update the configuration and memory system automatically. No files to edit.

## Frequently Asked Questions

**Q: Can the counterparty tell it's AI?**
The system is designed to mirror your communication style. Over time, populate the memory with your preferences and patterns.

**Q: What if there's a genuine emergency?**
Level 5 emergencies (threats, legal emergencies) bypass all protocols. The system escalates immediately to the principal.

**Q: Is this legal?**
Consult a licensed attorney in your jurisdiction. Laws about AI-generated communications vary. See [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md).

**Q: Can I use this for court documentation?**
The forensic archive system provides SHA-256 hash verification, but consult your attorney about admissibility in your jurisdiction.

**Q: What AI provider should I choose?**
- **Budget**: Ollama (free, runs locally)
- **Best quality**: Claude or GPT-4o
- **Fastest**: xAI Grok
- **Free cloud**: Google Gemini free tier

**Q: Can I add more contacts later?**
Yes. Edit `grey-rock-config.json` and add entries to the `contacts` array.

---

*This software is provided "AS IS" under the MIT License without warranty of any kind. Not legal advice. See [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) for complete terms. Copyright © 2026 johngalt2035-dev.*
