# Grey Rock

**Executive Assistant utilizing the Grey Rock communications protocol for managing high-conflict business correspondence via Signal, Telegram, WhatsApp, or SMS.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version: 5.0](https://img.shields.io/badge/version-5.0-orange)]()
[![Signal](https://img.shields.io/badge/Signal-supported-3a76f0)]()
[![Telegram](https://img.shields.io/badge/Telegram-supported-26a5e4)]()
[![WhatsApp](https://img.shields.io/badge/WhatsApp-supported-25d366)]()
[![SMS](https://img.shields.io/badge/SMS-supported-ff6b6b)]()

---

## What Is This?

A professional AI Executive Assistant that handles your high-conflict business communications — the same role performed by executive assistants, chiefs of staff, and communication managers who manage correspondence for principals across business, government, and legal contexts.

The system follows the [BIFF Response method](https://www.highconflictinstitute.com/biff-responses) (Eddy, 2014) and [Grey Rock technique](https://www.medicalnewstoday.com/articles/grey-rock) to compose brief, neutral, professional responses. Works with any AI provider (ChatGPT, Claude, Grok, Gemini, or local models) and any messaging platform (Signal, Telegram, WhatsApp, or SMS).

**Maximum truthfulness** — all communications are factually accurate. Deception in content is never permitted. The system simply handles correspondence professionally, as any competent Executive Assistant would.

## Who Is This For?

Anyone dealing with high-conflict individuals, groups, or business entities who communicates via messaging:

| Context | Use Case |
|---|---|
| **Opposing counsel / litigation counterparties** | Litigation logistics, dispute documentation, court-safe correspondence |
| **Hostile business partners** | Partnership disputes, financial disagreements, professional boundary enforcement |
| **Difficult clients or vendors** | Contract disputes, service disagreements, professional boundary management |
| **Contentious board members or investors** | Governance disputes, fiduciary disagreements, stakeholder management |
| **High-conflict colleagues or managers** | Workplace disputes, HR situations, professional boundary setting |
| **Demanding stakeholders** | Project disputes, scope conflicts, expectation management |
| **Anyone in a business context who escalates** | Contractors, landlords, regulatory counterparties, anyone who escalates |

## Getting Started

See **[SETUP.md](SETUP.md)** for a 5-minute setup guide. No technical background needed.

## Works With Any AI

| Provider | Models | Cost |
|----------|--------|------|
| **OpenAI** | GPT-4o, GPT-4o-mini | $$ |
| **Anthropic** | Claude Sonnet, Opus | $$ |
| **xAI** | Grok 4.1 | $ |
| **Google** | Gemini 2.5 Pro | Free-$$ |
| **Ollama** | Llama 3.2, Mistral | Free (local) |

See `templates/providers/` for provider-specific setup guides.

## Works With Any Platform

| Platform | Privacy | Setup |
|----------|---------|-------|
| **Signal** | End-to-end encrypted | Medium |
| **Telegram** | Cloud-based | Easy |
| **WhatsApp** | End-to-end encrypted | Hard |
| **SMS** | Via Twilio/AWS SNS | Medium |

See `templates/channels/` for platform-specific setup guides.

## Per-Contact Configuration

Different contacts get different treatment. One config file handles everything:

```json
{
  "contacts": [
    { "id": "opposing-counsel", "channels": ["signal", "sms"], "primary_channel": "signal", "protocol": "grey-rock", "communication_style": "executive" },
    { "id": "business-associate", "channels": ["sms"], "primary_channel": "sms", "protocol": "grey-rock", "communication_style": "personal" },
    { "id": "trusted-colleague", "channels": ["signal"], "primary_channel": "signal", "protocol": "normal", "communication_style": "personal" }
  ]
}
```

Grey rock contacts get BIFF responses. Normal contacts get natural communication.

### Communication Style Matrix

| Protocol | Style | Behavior |
|----------|-------|----------|
| **Grey Rock** | **Executive** | Formal BIFF. No contractions, complete sentences, legal-safe. "I will review that matter." |
| **Grey Rock** | **Personal** | Natural BIFF. Casual tone, contractions, shorthand. "Got it. I'll check." |
| **Normal** | **Executive** | Formal professional correspondence. Full sentences, titles, no shorthand. |
| **Normal** | **Personal** | Natural voice. Casual, direct, mirrors principal's trained patterns. |

## The Protocol

### BIFF Standard

Every response follows four rules:

| Rule | Meaning |
|------|---------|
| **B**rief | 1-2 sentences maximum. One word is often ideal. |
| **I**nformative | Only factual data — dates, times, locations, logistics. |
| **F**riendly | Neutral, professional tone. Never cold or aggressive. |
| **F**irm | Close the loop. No openings for further debate. |

### Anti-JADE Barrier

The agent is strictly forbidden from:
- **J**ustifying any action or decision
- **A**rguing any point
- **D**efending any position
- **E**xplaining any reasoning

If pressed: *"This is the current arrangement."* / *"I have nothing further to add on that."*

### Provocation Filter

When a message contains insults, accusations, guilt trips, or emotional bait:

1. **Ignore the bait entirely**
2. **Respond only to logistical content** (if any exists)
3. If no logistical content exists: *"Noted."*

### Response Templates

| Input Type | Response |
|---|---|
| Direct attack / insult | *"Noted. Regarding [task], I will [fact]."* |
| Demanding "Why?" | *"This is the current arrangement. Thank you."* |
| False accusation | *"I'd want to verify that. Nothing further to add."* |
| General drama / venting | *"I see. Any logistics to discuss?"* |
| Pure emotional (no logistics) | *"Noted."* |

### Acknowledgment Rotation

Every message must be acknowledged — never leave on read. Rotate naturally:

**Acknowledgments:** `check` · `got it` · `confirmed` · `noted` · `copy` · `understood` · `ok` · `roger`

**Affirmatives:** `that works` · `fine` · `sure` · `works for me` · `go ahead`

**Deferrals:** `I'll check on that` · `let me get back to you` · `I'll confirm later`

### Bail-Out Phrase

For circular conversations:

> *"Nothing further on that topic. Logistics?"*

Repeat verbatim as needed.

### Anti-DARVO Framework

**DARVO** = Deny, Attack, Reverse Victim and Offender. Multi-level response ladder:

| Phase | Response |
|---|---|
| Deny (first) | "I'd want to verify that. Let me check." |
| Deny (escalated) | "Nothing further on that." |
| Attack | Ignore. Logistics only. |
| Reverse V&O | "I see. Logistical matter?" |
| Full DARVO | Bail-out phrase |

### Legal Risk Framework

Every message may be read aloud in court. Apply the **Judge Test**: if a judge read this aloud, would it help, hurt, or be neutral? Only send if helps or neutral.

- Never admit fault (not "sorry", "my bad", or "moving forward")
- Never make threats, disparage, or use sarcasm
- Never discuss legal strategy
- Respond to every message (response expectations vary by jurisdiction; consult your attorney)

### Sensitive Matter Escalation

When a sensitive matter arises (legal, financial, regulatory), escalate to the principal for direct handling. The Executive Assistant flags these as [PRINCIPAL_REVIEW] for the principal's direct attention.

### Emergency Triage (5-Level)

| Level | Response |
|---|---|
| 1-3 (routine/request) | Grey rock |
| 4 (urgent business matter) | "Understood. What's the immediate need?" |
| 5 (threat / legal emergency) | Drop protocol. Full principal engagement. |

### Cluster B Pattern Recognition

Gaslighting, triangulation, love-bombing, splitting, manufactured urgency, emotional flooding, flying monkeys, manufactured obligation, hypothetical catastrophizing, selective memory, stealth requests, intermittent reinforcement — each with calibrated responses. See [PROTOCOL.md](docs/PROTOCOL.md).

### Invisible Side-Channel Draft Review

Every response goes through a private review channel before reaching the contact:
1. EA generates BIFF draft
2. Draft routed to your private review thread (Signal/Telegram/WhatsApp/SMS)
3. You approve, edit, reject, or escalate
4. Only approved responses sent to contact
5. Contact has zero visibility into the review process

Multi-reviewer chains supported for organizations (Principal → Legal → Final Approver).
See [PROTOCOL.md](docs/PROTOCOL.md) for full architecture.

### Hallucination Prevention

Hard rules to prevent LLM confabulation:
- Never confirm past commitments without deferring
- Never generate details about unverified events
- Never agree to financial amounts without deferring

### Information Blackout

Never share:
- Personal feelings or emotional state
- Future plans or goals
- New relationships or social activities
- Professional wins or accomplishments
- Financial details beyond logistics
- Health information beyond logistics
- Anything about your day, mood, or inner life

These are data points that can be weaponized.

### Shadow Logging

Archive all incoming messages with tags for record-keeping:
- `[LOGISTICS]` — schedule changes, requests, commitments, deadlines
- `[EMOTIONAL]` — emotional content, expressions of feeling (preserved as potential evidence)
- `[ESCALATION ALERT]` — threats, harassment, potential violence

### Daily Digest

Generate a logistics summary (emotional content preserved in full archive, summary extracts actionable items):
- Schedule changes
- Requests made
- Commitments or agreements
- Deadlines
- Action items requiring your attention
- Escalation alerts

### Escalation Scoring

Quantified 1-10 risk assessment tracking patterns across messages — volume, tone, channel escalation, third-party recruitment, and time-of-day shifts.

## Quick Start

### Generic (any LLM)

Copy `templates/generic/system-prompt.md` into your agent's system prompt.

### OpenClaw

Copy `templates/openclaw/SOUL.md` into your agent's workspace directory. See `examples/openclaw-config.json` for full instance configuration.

### Claude Code

Add the protocol to your `CLAUDE.md` or use `templates/claude-code/CLAUDE.md` as a starting point.

## File Structure

```
grey-rock-protocol/
├── README.md
├── LICENSE
├── templates/
│   ├── generic/
│   │   └── system-prompt.md        # Platform-agnostic system prompt
│   ├── openclaw/
│   │   ├── SOUL.md                 # OpenClaw agent identity file
│   │   └── cron-jobs.json          # Morning message + daily digest
│   └── claude-code/
│       └── CLAUDE.md               # Claude Code project instructions
├── examples/
│   └── openclaw-config.json        # Full OpenClaw instance config
└── docs/
    ├── PROTOCOL.md                 # Detailed protocol specification
    └── SAFETY.md                   # Safety considerations and limits
```

## Research Basis

This protocol is grounded in peer-reviewed behavioral psychology, clinical communications research, and high-conflict personality frameworks. See [docs/RESEARCH.md](docs/RESEARCH.md) for full evidence documentation with citations and limitations.

**Key finding**: Grey Rock and BIFF show strong anecdotal and clinical support but lack large-scale randomized controlled trials. Results vary by individual, context, and relationship history.

## Expected Outcomes & Realistic Timelines

Based on behavioral psychology literature (extinction research):
- **Weeks 2-8**: Reduced engagement typically begins; extinction bursts (temporary escalation) are common
- **Months 3-6**: Consistent application often shows measurable reduction in high-conflict patterns
- **Months 6-12+**: Long-term equilibrium depends on consistency, context, and the specific counterparty

These are general patterns from behavioral research, not guarantees. Individual results vary significantly.

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md) for planned features including implementation code, analytics, and evaluation suites.

## Contributing

We welcome contributions from communications researchers, psychologists, attorneys, and developers. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Safety Notice

Grey rocking is a **boundary management technique**, not a weapon. Important considerations:

- **Extinction bursts**: When a high-conflict individual stops getting emotional reactions, behavior may temporarily escalate. If threats occur, discontinue and seek legal counsel.
- **Not a substitute for legal counsel**: If you are in a high-conflict business dispute, litigation, or harassment situation, consult an attorney.
- **Not for threat situations**: If you are facing physical threats, contact law enforcement. Grey rocking does not protect against violence.

## Symbiotic System

Grey Rock Protocol is designed to work with [Grey Rock Memory](https://github.com/johngalt2035-dev/grey-rock-memory) as a symbiotic system. Both are built upon [OpenClaw](https://openclaw.ai).

| Component | Role |
|---|---|
| **Grey Rock Protocol** | Communication rules. BIFF templates. Anti-JADE/DARVO. Legal framework. |
| **[Grey Rock Memory](https://github.com/johngalt2035-dev/grey-rock-memory)** | Data backbone. Forensic archive. Escalation scoring. Training facility. SHA-256 chain. |
| **[OpenClaw](https://openclaw.ai)** | Agent orchestration. Channel routing. Cron scheduling. LLM management. |

## References

- Eddy, B. (2014). *BIFF: Quick Responses to High-Conflict People*. High Conflict Institute Press.
- [High Conflict Institute — BIFF Responses](https://www.highconflictinstitute.com/biff-responses)
- [Medical News Today — Grey Rock Method](https://www.medicalnewstoday.com/articles/grey-rock)

## Legal

### License

This software is licensed under the [MIT License](LICENSE).

### Disclaimer

**THIS SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.** The authors accept **zero liability** for any use, misuse, legal outcome, business outcome, or consequence arising from the use of this software.

**This is not legal advice.** This software does not constitute legal counsel or professional counsel of any kind. Consult a licensed attorney before implementing any communication strategy described herein.

**AI-generated communications.** Users are solely responsible for all consequences of AI-generated communications. Some jurisdictions may restrict or prohibit AI-generated communications in legal contexts.

See [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) for complete terms including assumption of risk, indemnification, AI-generated communication disclaimers, and jurisdictional notices.

---

*Copyright &copy; 2026 [johngalt2035-dev](https://github.com/johngalt2035-dev). MIT License. Built upon [OpenClaw](https://openclaw.ai). See [LICENSE](LICENSE) and [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md).*
