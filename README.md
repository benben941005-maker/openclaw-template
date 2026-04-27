# OpenClaw Configuration — Student Setup Guide

This folder contains the OpenClaw agent configuration. All sensitive values have been replaced with `xxx_..._xxx` placeholders. **You must fill in your own credentials before running.**

---

## Files You Need to Edit

### 1. `openclaw.json` — Main Config
**Path:** `.openclaw/openclaw.json`

| Field | Placeholder | What to put |
|-------|------------|-------------|
| `gateway.auth.token` | `xxx_GATEWAY_TOKEN_xxx` | Any random secret string (e.g. generate with `openssl rand -hex 24`) |
| `channels.telegram.botToken` | `xxx_TELEGRAM_BOT_TOKEN_xxx` | Your Telegram bot token from [@BotFather](https://t.me/BotFather) |
| `auth.profiles` email | `xxx_YOUR_EMAIL_xxx` | Your own email address |

---

### 2. `agents/main/agent/auth-profiles.json` — OpenAI Auth
**Path:** `.openclaw/agents/main/agent/auth-profiles.json`

| Field | Placeholder | What to put |
|-------|------------|-------------|
| `access` | `xxx_OPENAI_ACCESS_TOKEN_xxx` | Your OpenAI access token (obtained by logging into OpenAI Codex) |
| `refresh` | `xxx_OPENAI_REFRESH_TOKEN_xxx` | Your OpenAI refresh token |
| `email` | `xxx_YOUR_EMAIL_xxx` | Your email address |

> **How to get OpenAI tokens:** Run `openclaw auth login openai-codex` and follow the browser login flow. OpenClaw will fill these in automatically.

---

### 3. `media/inbound/client_secret_xxx.json` — Google OAuth
**Path:** `.openclaw/media/inbound/client_secret_xxx.json`

| Field | Placeholder | What to put |
|-------|------------|-------------|
| `client_id` | `xxx_GOOGLE_CLIENT_ID_xxx` | Your Google OAuth Client ID |
| `client_secret` | `xxx_GOOGLE_CLIENT_SECRET_xxx` | Your Google OAuth Client Secret |

> **How to get Google credentials:**
> 1. Go to [Google Cloud Console](https://console.cloud.google.com/)
> 2. Create a project → APIs & Services → Credentials
> 3. Create OAuth 2.0 Client ID (Desktop app)
> 4. Download the JSON and copy the values here

---

### 4. `credentials/telegram-default-allowFrom.json` — Telegram Allowed Users
**Path:** `.openclaw/credentials/telegram-default-allowFrom.json`

| Field | Placeholder | What to put |
|-------|------------|-------------|
| `allowFrom` array | `xxx_TELEGRAM_USER_ID_xxx` | Your Telegram user ID (get it from [@userinfobot](https://t.me/userinfobot)) |

---

### 5. `identity/device.json` & `identity/device-auth.json` — Device Identity
**Path:** `.openclaw/identity/`

These are auto-generated when you first run `openclaw`. You can **delete these files** and let OpenClaw regenerate them fresh on first launch.

| Placeholder | Notes |
|------------|-------|
| `xxx_DEVICE_ID_xxx` | Auto-generated — delete file to regenerate |
| `xxx_OPERATOR_TOKEN_xxx` | Auto-generated — delete file to regenerate |
| `xxx_PRIVATE_KEY_xxx` | Auto-generated — delete file to regenerate |
| `xxx_PUBLIC_KEY_xxx` | Auto-generated — delete file to regenerate |

---

## Quick Start

```bash
# 1. Copy this folder to your home directory
cp -r .openclaw ~/

# 2. Edit the main config with your credentials
nano ~/.openclaw/openclaw.json

# 3. Delete the device identity files (will be regenerated)
rm ~/.openclaw/identity/device.json
rm ~/.openclaw/identity/device-auth.json
rm ~/.openclaw/devices/paired.json

# 4. Log in to OpenAI (fills in auth-profiles.json automatically)
openclaw models auth login --provider openai-codex

# 5. Start the gateway
openclaw gateway
```

---

## Security Reminder

- **Never commit real tokens or API keys to GitHub**
- **Never share your `openclaw.json` with real credentials**
- Rotate any credentials that were accidentally exposed
- Add `.openclaw/agents/main/sessions/` to your `.gitignore`

---

## Placeholder Reference

| Placeholder | Description |
|------------|-------------|
| `xxx_GATEWAY_TOKEN_xxx` | OpenClaw gateway auth token |
| `xxx_TELEGRAM_BOT_TOKEN_xxx` | Telegram bot token from @BotFather |
| `xxx_TELEGRAM_BOT_ID_xxx` | Telegram bot numeric ID |
| `xxx_TELEGRAM_USER_ID_xxx` | Your personal Telegram user ID |
| `xxx_OPENAI_ACCESS_TOKEN_xxx` | OpenAI Codex access JWT |
| `xxx_OPENAI_REFRESH_TOKEN_xxx` | OpenAI Codex refresh token |
| `xxx_GOOGLE_CLIENT_ID_xxx` | Google OAuth 2.0 Client ID |
| `xxx_GOOGLE_CLIENT_SECRET_xxx` | Google OAuth 2.0 Client Secret |
| `xxx_YOUR_EMAIL_xxx` | Your email address |
| `xxx_DEVICE_ID_xxx` | Auto-generated device ID |
| `xxx_OPERATOR_TOKEN_xxx` | Auto-generated operator token |
| `xxx_PRIVATE_KEY_xxx` | Auto-generated private key |
| `xxx_PUBLIC_KEY_xxx` | Auto-generated public key |
