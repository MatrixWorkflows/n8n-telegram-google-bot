# Cleo - Personal AI Assistant Setup Guide

Cleo is a powerful personal AI assistant that runs on n8n and connects to Telegram, Gmail, Google Calendar, Google Sheets, Google Drive, Google Docs, Google Tasks, and more.

## Prerequisites

1. **n8n** - Self-hosted or cloud version
2. **Telegram Bot** - For chatting with Cleo
3. **Google Account** - For Gmail, Calendar, Sheets, Drive, Docs, Tasks
4. **OpenAI API Key** - For AI functionality

---

## Step 1: Install n8n

### Option A: Self-Hosted (Recommended)
```bash
# Using Docker
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  --env N8N_BASIC_AUTH_ACTIVE=true \
  --env N8N_BASIC_AUTH_USER=admin \
  --env N8N_BASIC_AUTH_PASSWORD=your_password \
  n8nio/n8n

# Using npm
npm install n8n -g
n8n start
```

### Option B: n8n Cloud
Sign up at [n8n.io](https://n8n.io)

---

## Step 2: Create Telegram Bot

1. Open Telegram and search for **@BotFather**
2. Send `/newbot` command
3. Follow instructions to name your bot
4. Copy the **Bot Token** (looks like: `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`)

---

## Step 3: Set Up Google Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project
3. Enable these APIs:
   - Gmail API
   - Google Calendar API
   - Google Drive API
   - Google Sheets API
   - Google Docs API
   - Google Tasks API
4. Go to **Credentials** → **Create Credentials** → **OAuth 2.0 Client ID**
5. Set application type to **Desktop App**
6. Download the JSON credentials file
7. In n8n: Go to **Settings** → **Credentials** → **New** → **Google OAuth2**
8. Paste the credentials

---

## Step 4: Set Up OpenAI API

1. Go to [OpenAI Platform](https://platform.openai.com)
2. Create an API key
3. In n8n: **Settings** → **Credentials** → **New** → **OpenAI API**

---

## Step 5: Import Workflows

1. Open n8n
2. Click **Import from File**
3. Import these workflow files:
   - `Cleo Brain.json` (main workflow - Telegram bot)
   - `Gmail Agent.json`
   - `Google Sheets AI Agent.json`
   - `Docs.json`
   - `Drive.json`
   - `Tasks.json`
   - `Smart Reminder.json`
   - `Memory Pipeline.json`
   - `Cleo Brain.json` (or `Cleo.json`)

---

## Step 6: Configure Credentials

For each workflow, you'll need to set up credentials:

1. Open each workflow in n8n
2. Click on nodes that show a ⚠️ warning
3. Select or create the appropriate credential:
   - **Telegram API** → Your Telegram bot token
   - **Google OAuth2** → Your Google account
   - **OpenAI API** → Your OpenAI API key

---

## Step 7: Configure Custom Values

### Google Doc ID (for Docs.json)
In the `Append_Notes` node:
- Replace `{{YOUR_GOOGLE_DOC_ID}}` with your Google Doc ID
- To find: Open your doc → Copy the ID from URL: `docs.google.com/document/d/YOUR_DOC_ID/edit`

### Timezone
All workflows use `Asia/Kolkata` timezone. To change:
- Search for `Asia/Kolkata` in each file
- Replace with your timezone (e.g., `America/New_York`, `Europe/London`)

---

## Step 8: Connect Telegram to Cleo

1. In n8n, open `Cleo Brain.json`
2. Find the **Telegram Trigger** node
3. Click **Test workflow** to get the webhook URL
4. Set the webhook:
   - Open Telegram, talk to @BotFather
   - Send `/setwebhook`
   - Enter your webhook URL: `https://your-n8n-url.com/webhook/50c4c642-0172-4ea9-a95f-99f74a752264`

---

## Available Commands

Once set up, you can chat with Cleo on Telegram:

- **Chat naturally** - Just talk to Cleo
- `/start` - Welcome message
- `/help` - Help menu
- `/clear` - Clear conversation history

### What Cleo Can Do

- **📅 Calendar** - "Schedule a meeting tomorrow at 3pm"
- **📧 Email** - "Send an email to john@example.com"
- **📝 Notes** - "Note: wifi password is ABC123"
- **✅ Reminders** - "Remind me to call John at 5pm"
- **📊 Sheets** - "Create a spreadsheet for expenses"
- **☁️ Drive** - "Upload this to Drive"
- **🔍 Wikipedia** - "Look up quantum computing"

---

## Troubleshooting

### "Node is not authenticated"
- Go to **Settings** → **Credentials**
- Make sure all credentials are properly configured
- Re-authorize Google OAuth if needed

### Telegram not responding
- Check the webhook is set correctly
- Make sure the workflow is **Active**
- Check n8n logs for errors

### AI not responding
- Verify OpenAI API key is set
- Check API credits at OpenAI dashboard
