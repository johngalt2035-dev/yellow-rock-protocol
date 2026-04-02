# Messaging Platform Setup Guides

Grey Rock supports multiple messaging platforms. Choose the one(s) your contacts use.

## Signal

**Privacy**: End-to-end encrypted. Best for sensitive communications.
**Setup difficulty**: Medium (requires signal-cli)

### Setup
1. Install signal-cli: `brew install signal-cli` (Mac) or download from [github.com/AsamK/signal-cli](https://github.com/AsamK/signal-cli)
2. Link as a secondary device:
   ```bash
   signal-cli link -n "grey-rock"
   ```
3. Scan the QR code with Signal on your phone (Settings > Linked Devices)
4. In config:
   ```json
   "signal": { "enabled": true, "account": "+1XXXXXXXXXX" }
   ```

### Platform Notes
- Messages are end-to-end encrypted
- Receipts can be enabled/disabled
- Group messages can be disabled (recommended)
- Images/media received but not processed (text only)

---

## Telegram

**Privacy**: Cloud-based (not E2E by default). Server-side encryption.
**Setup difficulty**: Easy (BotFather creates bot in seconds)

### Setup
1. Open Telegram and message [@BotFather](https://t.me/BotFather)
2. Send `/newbot` and follow the prompts
3. Copy the bot token
4. In config:
   ```json
   "telegram": { "enabled": true, "bot_token": "123456:ABC-DEF..." }
   ```

### Platform Notes
- Bot receives all messages sent to it
- Can be added to groups
- Supports inline keyboards and rich formatting
- Not end-to-end encrypted by default (use Secret Chats for E2E)
- Widely used internationally

---

## WhatsApp

**Privacy**: End-to-end encrypted. Most widely used globally.
**Setup difficulty**: Hard (requires WhatsApp Business API)

### Setup
1. Apply for WhatsApp Business API access via [Meta for Developers](https://developers.facebook.com/docs/whatsapp/)
2. Set up a business phone number
3. Get an API token
4. In config:
   ```json
   "whatsapp": { "enabled": true, "business_phone": "+1XXXXXXXXXX", "api_token": "..." }
   ```

### Platform Notes
- Requires Meta Business verification
- Monthly costs apply for Business API
- End-to-end encrypted
- Most widely used messaging platform globally
- Some regions require this for communication

### Alternative: WhatsApp Web Bridge
For personal use without Business API, community bridges like [whatsmeow](https://github.com/tulir/whatsmeow) can connect WhatsApp Web. Note: this may violate WhatsApp ToS.

---

## SMS

**Privacy**: Not encrypted. Standard carrier messaging.
**Setup difficulty**: Medium (requires Twilio, AWS SNS, or VoIP.ms)

### Option A: Twilio Setup

1. Create a Twilio account at [twilio.com](https://www.twilio.com/)
2. Get your Account SID and Auth Token from the Twilio Console
3. Purchase a phone number with SMS capability
4. Set environment variables:
   ```bash
   export TWILIO_ACCOUNT_SID="ACxxxxxxxxxx"
   export TWILIO_AUTH_TOKEN="your_auth_token"
   ```
5. In config:
   ```json
   "sms": { "enabled": true, "provider": "twilio", "account_sid_env": "TWILIO_ACCOUNT_SID", "auth_token_env": "TWILIO_AUTH_TOKEN", "phone_number": "+1XXXXXXXXXX" }
   ```

### Option B: AWS SNS Setup

1. Configure AWS CLI with appropriate IAM credentials
2. Select your preferred AWS region for SMS
3. Provision a phone number via Amazon Pinpoint or SNS
4. Set up IAM policy with `sns:Publish` permission
5. In config:
   ```json
   "sms": { "enabled": true, "provider": "aws_sns", "region": "us-east-1", "phone_number": "+1XXXXXXXXXX" }
   ```

### Option C: VoIP.ms Setup

1. Create a VoIP.ms account at [voip.ms](https://voip.ms/)
2. Purchase a DID (phone number) with SMS enabled
3. Enable SMS on the DID in the VoIP.ms portal
4. Get your API credentials (email + API password)
5. In config:
   ```json
   "sms": { "enabled": true, "provider": "voipms", "api_user_env": "VOIPMS_USER", "api_pass_env": "VOIPMS_PASS", "did": "+1XXXXXXXXXX" }
   ```

### TCPA Compliance Notice

SMS messaging is subject to the Telephone Consumer Protection Act (TCPA) in the United States and equivalent regulations in other jurisdictions. You are responsible for compliance with all applicable laws governing automated or AI-assisted text messaging. Consult a licensed attorney for jurisdiction-specific guidance.

### Platform Notes
- SMS is not encrypted in transit
- Delivery receipts may not be reliable across all carriers
- Message length limited to 160 characters per segment (longer messages split automatically)
- MMS (media) not supported — text only
- Widely supported across all phones without app installation

---

## Platform Comparison

| Feature | Signal | Telegram | WhatsApp | SMS |
|---------|--------|----------|----------|-----|
| **E2E Encryption** | Always | Optional | Always | Never |
| **Setup Difficulty** | Medium | Easy | Hard | Medium |
| **Cost** | Free | Free | Business API fees | Per-message fees |
| **Group Support** | Yes | Yes | Yes | No |
| **Media Processing** | Text only | Text only | Text only | Text only |
| **Global Availability** | Good | Good | Best | Best |
| **Privacy** | Best | Medium | Good | Low |
| **Bot Support** | Via signal-cli | Native (BotFather) | Via Business API | Via Twilio/AWS SNS/VoIP.ms |

## Multi-Platform Setup

You can enable multiple platforms simultaneously. Each contact in your config specifies which platform they use:

```json
"contacts": [
  { "id": "opposing-counsel", "channels": ["signal", "sms"], "primary_channel": "signal", "protocol": "grey-rock" },
  { "id": "neighbor", "channels": ["whatsapp"], "primary_channel": "whatsapp", "protocol": "grey-rock" },
  { "id": "coworker", "channels": ["telegram", "sms"], "primary_channel": "telegram", "protocol": "grey-rock" }
]
```

The system routes messages to the correct platform automatically based on the contact's `primary_channel` setting. When a contact has multiple channels configured, the system uses the primary channel by default and can fall back to secondary channels if needed.
