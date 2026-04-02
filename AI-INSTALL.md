# AI-Assisted Installation

Let your AI assistant install Yellow Rock for you. Copy-paste one prompt, and your AI does the rest.

> **Documentation Map**: [INSTALL.md](INSTALL.md) (manual install) → You are here → **AI-INSTALL.md** → [SETUP.md](SETUP.md) (configure contacts)

> **Which AI can install this?**
> - **OpenClaw**: Full automated setup (best option if you have OpenClaw) — [install OpenClaw](https://openclaw.ai)
> - **Claude Code**: Can clone, build, and configure directly on your machine
> - **ChatGPT / OpenAI**: Can generate commands for you to copy-paste (cannot execute directly)
> - **Any AI with terminal access**: Copy the prompts below and paste them into your AI

---

## Method 1: OpenClaw

If you have [OpenClaw](https://openclaw.ai) running, tell your agent:

```
Install the Yellow Rock Executive Assistant communication system from these two repositories:
- https://github.com/johngalt2035-dev/yellow-rock-protocol (communication templates)
- https://github.com/johngalt2035-dev/yellow-rock-memory (memory + forensic archive)

Steps:
1. Clone both repos
2. Build yellow-rock-memory: cargo build --release
3. Install the binary to /usr/local/bin/
4. Start the yellow-rock-memory daemon on port 9077
5. Copy templates/openclaw/SOUL.md to my agent workspace
6. Replace {{USER_NAME}} with my name, {{CONTACT_NAME}} with the counterparty's name
7. Replace {{CHANNEL}} with "signal" (or telegram/whatsapp)
8. Copy templates/openclaw/cron-jobs.json for automated daily digest
9. Configure my channel binding to route messages to the yellow-rock agent
10. Test by sending a message to my own number (Note to Self)
```

### Setting Communication Style via OpenClaw

```
Set my communication style to executive for opposing-counsel and personal for trusted-colleague.

Generate training data for both styles:
- Personal: my natural texting patterns (casual, contractions, shorthand)
- Executive: formal correspondence patterns (no contractions, titles, full sentences)

Import the training data into yellow-rock-memory.
```

### Adding Training Data via OpenClaw

```
Load the following background data into the Yellow Rock Memory system:

yellow-rock-memory --db ~/.yellow-rock/memory.db train [FILE]

Create a training file with these facts:
- [Contact name] works [schedule]
- Key deadlines: [list]
- [Any other facts the AI should know]

Import it and verify with: yellow-rock-memory --db ~/.yellow-rock/memory.db stats
```

### Adding Contacts via OpenClaw

```
Add a new yellow-rock contact:
- Name: [Their Name]
- Phone: [Their Number]
- Channel: signal (or telegram/whatsapp)
- Protocol: yellow-rock (BIFF responses, logging, escalation tracking)

Update the openclaw.json allowFrom list to include their number.
Update the SOUL.md to include their contact_id for memory routing.
```

---

## Method 2: Claude Code

Open Claude Code in any project directory and say:

```
I want to set up the Yellow Rock Executive Assistant communication system.
I am on [macOS / Windows / Ubuntu / Fedora].

1. Clone https://github.com/johngalt2035-dev/yellow-rock-memory
2. Build it: cd yellow-rock-memory && cargo build --release
   (Note: this takes 5-20 minutes the first time — that's normal)
3. Install the binary:
   - macOS Apple Silicon: cp target/release/yellow-rock-memory /opt/homebrew/bin/
   - macOS Intel: cp target/release/yellow-rock-memory /usr/local/bin/
   - Linux: cp target/release/yellow-rock-memory /usr/local/bin/
   - Windows: copy target\release\yellow-rock-memory.exe $env:USERPROFILE\bin\
   (Do NOT use sudo — if permission denied, use cp to ~/bin/ instead)
4. Create database: mkdir -p ~/.yellow-rock
5. Start daemon: yellow-rock-memory --db ~/.yellow-rock/memory.db serve --port 9077
6. Verify: curl http://localhost:9077/api/v1/health

Then clone the protocol:
7. Clone https://github.com/johngalt2035-dev/yellow-rock-protocol
8. Copy templates/claude-code/CLAUDE.md to my project root
9. Replace [CONTACT_NAME] with: [TYPE THE COUNTERPARTY'S NAME HERE]

Now I want to train it with background data. Create a JSON file with these facts:
- [List your facts here, e.g.:]
- Contact's business hours: Mon-Fri 9-5
- Key deadlines and milestones
- Known escalation triggers: financial disputes, deadline changes

Import with: yellow-rock-memory --db ~/.yellow-rock/memory.db train [filename].json
Verify with: yellow-rock-memory --db ~/.yellow-rock/memory.db stats
```

> **Note**: Claude Code runs commands directly on your machine. If a `sudo` command fails (password required), Claude Code will suggest an alternative path that doesn't need sudo.

### Setting Communication Style via Claude Code

```
Set my communication style to [personal/executive] for each contact in yellow-rock-config.json.

Generate communication style training data:
- For personal style: capture my natural texting voice (contractions, casual tone, shorthand)
- For executive style: formal professional patterns (no contractions, full sentences, titles)

Create the training JSON and import it with:
yellow-rock-memory --db ~/.yellow-rock/memory.db train style-training.json
```

### Adding Training Data via Claude Code

```
Create a training file for yellow-rock-memory with these facts about my situation:
- Key counterparty details: [describe]
- Contact's business hours: [describe]
- Important deadlines: [describe]
- Relevant agreements or contracts: [list]

Format as JSON array of {title, content, tags, priority} objects.
Then import: yellow-rock-memory --db ~/.yellow-rock/memory.db train training.json
```

### Adding Contacts via Claude Code

```
I want to add a new high-conflict contact to Yellow Rock:
- Name: [name]
- Their phone: [number]
- Platform: [signal/telegram/whatsapp]

Update my yellow-rock-config.json to add them as a yellow-rock protocol contact.
Generate appropriate training data for this contact and import it.
```

---

## Method 3: ChatGPT / OpenAI

> **Important**: ChatGPT runs in a cloud sandbox — it **cannot** install software on your computer. Instead, it will **generate the exact commands** for you to copy-paste into your terminal. This is still very helpful — it's like having an expert write your installation script.

In ChatGPT:

```
Help me install the Yellow Rock Executive Assistant communication system.

Repositories:
- Protocol (templates): https://github.com/johngalt2035-dev/yellow-rock-protocol
- Memory (Rust daemon): https://github.com/johngalt2035-dev/yellow-rock-memory

I'm on [macOS/Windows/Ubuntu/Fedora].

Please:
1. Give me the exact commands to clone, build, and install yellow-rock-memory
2. Show me how to start the daemon
3. Help me create a configuration file for my contacts
4. Help me create training data with my situation's background facts
5. Show me how to verify everything works
```

### Setting Communication Style via ChatGPT

```
Help me configure communication styles for Yellow Rock Protocol.

I want:
- Executive style for: [list contacts in litigation/formal disputes]
- Personal style for: [list trusted/casual contacts]

Generate training data JSON for both styles based on my communication patterns:
- Personal: [describe your texting style, e.g., "I use lots of abbreviations, no caps, very brief"]
- Executive: [describe your formal style, e.g., "I address people as Mr./Ms., sign off with Regards"]

Then give me the command to import it into yellow-rock-memory.
```

### Adding Training Data via ChatGPT

```
I need to create training data for Yellow Rock Memory.
Here's my situation:
- [Describe your business conflict/context]
- [Key schedules and deadlines]
- [Important facts]

Generate a background.json file in this format:
[{"title": "...", "content": "...", "tags": [...], "priority": N}, ...]

Then give me the command to import it.
```

---

## Testing Without Real Contacts

**IMPORTANT**: Never test with real contacts. Always test with yourself first.

### Quick Smoke Test (30 seconds)

Run this single command to verify everything works:

```bash
# Mac / Linux:
curl -s http://localhost:9077/api/v1/health && echo " ← If you see 'ok', the system is running!"

# Windows (PowerShell):
(Invoke-WebRequest http://localhost:9077/api/v1/health).Content
# Should show: {"status":"ok","service":"yellow-rock-memory"}
```

If that works, the system is live. Now test the full pipeline:

### Signal — Test with Note to Self

```bash
# Send a test message to your own Note to Self
signal-cli -a +YOUR_NUMBER send --note-to-self -m "Test: Meeting confirmed for 3pm"

# Verify the system responds (if connected to an AI agent)
# Or manually test the memory system:
curl -X POST http://localhost:9077/api/v1/messages \
  -H 'Content-Type: application/json' \
  -d '{"sender":"test-contact","contact_id":"test","raw_content":"Meeting confirmed for 3pm","category":"LOGISTICS"}'

# Check it was archived
yellow-rock-memory --db ~/.yellow-rock/memory.db stats

# Check escalation (should be 1/ROUTINE for one message)
curl "http://localhost:9077/api/v1/escalation?contact_id=test"

# Generate digest
curl "http://localhost:9077/api/v1/digest?contact_id=test"
```

### Telegram — Test with BotFather

```bash
# 1. Message your bot directly in Telegram
# 2. Check bot received it via getUpdates:
curl "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates"

# 3. Test memory archival:
curl -X POST http://localhost:9077/api/v1/messages \
  -H 'Content-Type: application/json' \
  -d '{"sender":"telegram-test","contact_id":"test","channel":"telegram","raw_content":"Test message","category":"LOGISTICS"}'
```

### WhatsApp — Test with WhatsApp Business Test Number

```bash
# WhatsApp Business API provides test phone numbers
# Use the test number from your Meta Developer dashboard

# Test memory archival:
curl -X POST http://localhost:9077/api/v1/messages \
  -H 'Content-Type: application/json' \
  -d '{"sender":"whatsapp-test","contact_id":"test","channel":"whatsapp","raw_content":"Test message","category":"LOGISTICS"}'
```

### Verify Full Pipeline (All Platforms)

```bash
# 1. Archive a test message
curl -X POST http://localhost:9077/api/v1/messages \
  -H 'Content-Type: application/json' \
  -d '{"sender":"test","contact_id":"pipeline-test","raw_content":"This is completely unacceptable and you will hear from my attorney","category":"NOISE","escalation_score":4}'

# 2. Archive another
curl -X POST http://localhost:9077/api/v1/messages \
  -H 'Content-Type: application/json' \
  -d '{"sender":"test","contact_id":"pipeline-test","raw_content":"The deliverable is due Thursday at 5pm","category":"LOGISTICS","extracted_logistics":"deliverable due 5pm Thursday"}'

# 3. Check escalation
curl "http://localhost:9077/api/v1/escalation?contact_id=pipeline-test"
# Should return score with NOISE factored in

# 4. Get digest (logistics only)
curl "http://localhost:9077/api/v1/digest?contact_id=pipeline-test"
# Should return only the logistics message, not the noise

# 5. Verify DB integrity
yellow-rock-memory --db ~/.yellow-rock/memory.db verify-db
# Should return: ALL HASHES VALID

# 6. Test forensic archive
yellow-rock-memory --db ~/.yellow-rock/memory.db archive-messages -o /tmp/test-archive.json
yellow-rock-memory verify-archive /tmp/test-archive.json
# Should return: VALID

# 7. Clean up test data
yellow-rock-memory --db ~/.yellow-rock/memory.db forget --namespace yellow-rock --pattern "pipeline-test"
rm /tmp/test-archive.json
```

---

## After Testing: Go Live

1. Remove all test data: `yellow-rock-memory --db ~/.yellow-rock/memory.db forget --pattern "test"`
2. Load real training data: `yellow-rock-memory --db ~/.yellow-rock/memory.db train your-data.json`
3. Configure real contacts in `yellow-rock-config.json`
4. Enable channel (Signal/Telegram/WhatsApp/SMS) in your AI platform
5. Monitor: `curl http://localhost:9077/api/v1/stats` daily

---

*Yellow Rock Memory and [Yellow Rock Protocol](https://github.com/johngalt2035-dev/yellow-rock-protocol) work together as a symbiotic system, built upon [OpenClaw](https://openclaw.ai).*

---

*This software is provided "AS IS" under the MIT License without warranty of any kind. Not legal advice. See [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) for complete terms. Copyright © 2026 johngalt2035-dev.*
