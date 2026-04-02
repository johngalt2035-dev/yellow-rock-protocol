# Installation Guide

Install the Yellow Rock Protocol on any platform. These are communication templates — no compilation needed, no programming required.

> **No technical experience?** Skip to [AI-Assisted Installation](AI-INSTALL.md) — let ChatGPT, Claude, or your AI assistant do it for you.

> **Documentation Map**: You are here → **INSTALL.md** (get the files). Next → [SETUP.md](SETUP.md) (configure). Then → [AI-INSTALL.md](AI-INSTALL.md) (connect + test). Companion → [Yellow Rock Memory](https://github.com/johngalt2035-dev/yellow-rock-memory) (forensic archive system).

---

## What You're Installing

Yellow Rock Protocol is a set of **text files** (templates) that tell your AI Executive Assistant how to respond to high-conflict individuals, groups, or business entities. There's nothing to compile or build — just download and use.

---

## macOS

Open **Terminal** (Applications > Utilities > Terminal):

```bash
# Install git if needed (a popup may appear — click Install)
xcode-select --install

# Download the protocol
git clone https://github.com/johngalt2035-dev/yellow-rock-protocol.git
cd yellow-rock-protocol

# View the main template
cat templates/generic/system-prompt.md

# Copy to clipboard
cat templates/generic/system-prompt.md | pbcopy
echo "Template copied to clipboard! Paste it into your AI."
```

---

## Windows

Open **PowerShell** (search Start menu for "PowerShell"):

```powershell
# Install git if needed — download from https://git-scm.com/ first

# Download the protocol
git clone https://github.com/johngalt2035-dev/yellow-rock-protocol.git
cd yellow-rock-protocol

# View the main template
Get-Content templates\generic\system-prompt.md

# Copy to clipboard
Get-Content templates\generic\system-prompt.md | Set-Clipboard
Write-Host "Template copied to clipboard! Paste it into your AI."
```

**Don't have git?** Use Option B below (ZIP download — no git needed).

---

## Ubuntu / Debian

```bash
# Install git if needed
sudo apt update && sudo apt install -y git

# Download the protocol
git clone https://github.com/johngalt2035-dev/yellow-rock-protocol.git
cd yellow-rock-protocol

# Copy to clipboard (install xclip first)
sudo apt install -y xclip
cat templates/generic/system-prompt.md | xclip -selection clipboard
echo "Template copied to clipboard!"
```

---

## Fedora / RHEL

```bash
sudo dnf install -y git
git clone https://github.com/johngalt2035-dev/yellow-rock-protocol.git
cd yellow-rock-protocol
cat templates/generic/system-prompt.md
```

---

## No Git? Download ZIP Instead

1. Go to [github.com/johngalt2035-dev/yellow-rock-protocol](https://github.com/johngalt2035-dev/yellow-rock-protocol)
2. Click the green **"<> Code"** button
3. Click **"Download ZIP"**
4. Extract the ZIP to any folder
5. Open the `templates/generic/system-prompt.md` file in any text editor

---

## How to Use the Templates

### With ChatGPT (OpenAI)

1. Go to [chatgpt.com](https://chatgpt.com)
2. Click your profile icon → **Customize ChatGPT** (or create a custom GPT)
3. In "What would you like ChatGPT to know?" or "System instructions", paste the contents of `templates/generic/system-prompt.md`
4. Find `[CONTACT_NAME]` in the text and replace with the counterparty's name
5. Save. Start chatting — ask it to draft responses to their messages.

### With Claude (Anthropic)

1. Go to [claude.ai](https://claude.ai) or open Claude Code
2. Start a new project or conversation
3. Paste `templates/generic/system-prompt.md` (or for Claude Code, copy `templates/claude-code/CLAUDE.md` to your project root)
4. Replace `[CONTACT_NAME]` with the counterparty's name
5. Paste their messages and ask Claude to draft responses

### With Grok (xAI)

1. Go to [grok.x.ai](https://grok.x.ai) or use the API
2. Paste `templates/generic/system-prompt.md` as the system message
3. Replace `[CONTACT_NAME]` and start drafting responses

### With Gemini (Google)

1. Go to [gemini.google.com](https://gemini.google.com) or use AI Studio
2. Paste `templates/generic/system-prompt.md` into the system instructions
3. Replace `[CONTACT_NAME]` and start drafting

### With Ollama (Local / Free / Private)

```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Download a model
ollama pull llama3.2:8b

# Run with the Yellow Rock system prompt
ollama run llama3.2:8b --system "$(cat templates/generic/system-prompt.md)"
```

Replace `[CONTACT_NAME]` in the prompt when it starts.

### Communication Style Training

Train the memory system with your communication patterns for each style.

**Personal style training** — teach the AI your natural voice:
```json
[
  { "title": "Personal style patterns", "content": "Uses contractions (I'll, won't, can't). Short sentences. Casual openers (hey, hi). Signs off with first name or no sign-off. Prefers lowercase in texts. Direct and to the point." },
  { "title": "Personal acknowledgments", "content": "Typical acks: got it, cool, works for me, sounds good, sure thing, k." }
]
```

**Executive style training** — formal professional patterns:
```json
[
  { "title": "Executive style patterns", "content": "No contractions. Complete sentences. Professional salutations (Dear Mr./Ms.). Formal closings (Regards, Best regards). Address counterparties by title and surname." },
  { "title": "Executive acknowledgments", "content": "Typical acks: Acknowledged, Confirmed, Understood, Thank you for confirming." }
]
```

Import with: `yellow-rock-memory --db ~/.yellow-rock/memory.db train style-training.json`

### With OpenClaw (Full Automation)

1. Copy `templates/openclaw/SOUL.md` to your OpenClaw agent workspace
2. Replace `{{USER_NAME}}`, `{{CONTACT_NAME}}`, `{{CHANNEL}}`
3. Copy `templates/openclaw/cron-jobs.json` for automated morning messages + daily digest
4. Configure channel bindings in `openclaw.json`

See the [OpenClaw documentation](https://openclaw.ai) for details.

---

## Configuration

After installing, copy and edit the config file:

```bash
# Copy the template
cp templates/config/yellow-rock-config.json ~/yellow-rock-config.json

# Edit it with any text editor
# macOS: open -e ~/yellow-rock-config.json
# Windows: notepad $env:USERPROFILE\yellow-rock-config.json
# Linux: nano ~/yellow-rock-config.json
```

See [SETUP.md](SETUP.md) for what each field means.

---

## Set Your API Key

If using an AI provider that requires an API key:

**macOS** (add to `~/.zshrc`):
```bash
echo 'export OPENAI_API_KEY="sk-your-key-here"' >> ~/.zshrc
source ~/.zshrc
```

**Linux** (add to `~/.bashrc`):
```bash
echo 'export OPENAI_API_KEY="sk-your-key-here"' >> ~/.bashrc
source ~/.bashrc
```

**Windows** (PowerShell):
```powershell
[Environment]::SetEnvironmentVariable("OPENAI_API_KEY", "sk-your-key-here", "User")
# Restart PowerShell after setting
```

Replace `OPENAI_API_KEY` with `ANTHROPIC_API_KEY`, `XAI_API_KEY`, or `GOOGLE_API_KEY` for other providers.

---

## What's Inside

```
yellow-rock-protocol/
├── templates/
│   ├── generic/system-prompt.md      # Works with ANY AI ← start here
│   ├── claude-code/CLAUDE.md         # Claude Code project file
│   ├── openclaw/SOUL.md              # OpenClaw agent identity
│   ├── openclaw/cron-jobs.json       # Automated jobs
│   ├── config/yellow-rock-config.json  # Configuration template
│   ├── providers/README.md           # AI provider setup guides
│   └── channels/README.md            # Messaging platform guides
├── docs/
│   ├── PROTOCOL.md                   # Full protocol specification
│   └── SAFETY.md                     # Safety considerations
├── INSTALL.md                        # This file
├── SETUP.md                          # 5-minute configuration guide
├── AI-INSTALL.md                     # AI-assisted installation
├── LEGAL_DISCLAIMER.md               # Legal terms
└── LICENSE                           # MIT License
```

---

## Companion: Yellow Rock Memory

For forensic message archival, escalation tracking, and SHA-256 evidentiary chain, install [Yellow Rock Memory](https://github.com/johngalt2035-dev/yellow-rock-memory). See its [INSTALL.md](https://github.com/johngalt2035-dev/yellow-rock-memory/blob/main/INSTALL.md) for platform-specific instructions.

The protocol (templates) + memory (database) work together as a symbiotic system, both built upon [OpenClaw](https://openclaw.ai).

---

## Troubleshooting

**"git: command not found"**
- macOS: `xcode-select --install`
- Windows: Download from [git-scm.com](https://git-scm.com/)
- Ubuntu: `sudo apt install git`
- Fedora: `sudo dnf install git`

**"I don't want to use git"**
- Use the ZIP download option above — no git needed

**"Which template do I use?"**
- **Any AI** (ChatGPT, Claude, Grok, Gemini): `templates/generic/system-prompt.md`
- **Claude Code**: `templates/claude-code/CLAUDE.md`
- **OpenClaw**: `templates/openclaw/SOUL.md`
- **Local (Ollama)**: `templates/generic/system-prompt.md` with `--system` flag

**"How do I replace [CONTACT_NAME]?"**
- Open the file in any text editor (Notepad, TextEdit, nano, VS Code)
- Find `[CONTACT_NAME]` or `{{CONTACT_NAME}}`
- Replace every occurrence with the actual counterparty's name
- Save the file

---

## Next Steps

1. **Configure your contacts** → [SETUP.md](SETUP.md)
2. **Connect to your AI + test** → [AI-INSTALL.md](AI-INSTALL.md)
3. **Install the memory system** → [Yellow Rock Memory INSTALL.md](https://github.com/johngalt2035-dev/yellow-rock-memory/blob/main/INSTALL.md)

---

*Yellow Rock Protocol works with [Yellow Rock Memory](https://github.com/johngalt2035-dev/yellow-rock-memory). Both are built upon [OpenClaw](https://openclaw.ai). See [LICENSE](LICENSE) and [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) for terms.*

---

*This software is provided "AS IS" under the MIT License without warranty of any kind. Not legal advice. See [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) for complete terms. Copyright © 2026 johngalt2035-dev.*
