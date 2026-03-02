# n8n-telegram-google-bot
Telegram bot powered by n8n that controls Gmail, Google Calendar, Drive ect. processes PDFs/text files

Markdown

# 🧠 Cleo - Self-Hosted Personal AI Assistant

> **An open-source, privacy-first AI operating system built on n8n that transforms Telegram into your personal command center for Gmail, Calendar, Drive, Docs, Sheets, Tasks, and more.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![n8n](https://img.shields.io/badge/Built%20with-n8n-FF6D5A)](https://n8n.io)
[![Telegram](https://img.shields.io/badge/Platform-Telegram-blue)](https://telegram.org)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

## 🎯 What is Cleo?

Cleo is a **multi-agent AI system** that gives you natural language control over your entire digital workspace — all through Telegram chat. No apps, no context switching, just conversation.

**Think of it as your personal Jarvis, but:**
- ✅ Fully self-hosted (your data never leaves your server)
- ✅ Open source (MIT licensed)
- ✅ Extensible (built on n8n's visual workflow engine)
- ✅ Privacy-first (no third-party AI services can see your data)

---

## ✨ Features

### 🤖 **Multi-Agent Architecture**
Cleo runs **8 specialized AI agents**, each handling different domains:

| Agent | Capabilities |
|-------|-------------|
| **📧 Gmail Agent** | Read, send, search, draft emails with context |
| **📅 Calendar Agent** | Schedule, reschedule, find availability |
| **📊 Sheets Agent** | Create spreadsheets, log data, generate reports |
| **📝 Docs Agent** | Append notes, create documents, search content |
| **☁️ Drive Agent** | Upload files, organize folders, search files |
| **✅ Tasks Agent** | Create, complete, prioritize tasks |
| **⏰ Smart Reminder** | Context-aware reminders with follow-ups |
| **🧠 Memory Pipeline** | Persistent conversation context across sessions |

### 💬 Natural Language Interface
You: "Schedule coffee with Sarah tomorrow at 3pm and email her the invite"

Cleo: ✅ Created calendar event for tomorrow 3pm
✅ Sent email to sarah@example.com with calendar invite
✅ Set reminder 30 mins before

You: "What were the action items from last week's meeting notes?"

Cleo: 📋 Analyzing your Docs...
Found 3 action items:
• Follow up with vendor (Due: Friday)
• Review Q1 budget spreadsheet
• Schedule team sync

text


### 🔐 Privacy-First Design
- **Self-hosted**: Runs on your infrastructure (Docker, VPS, or local)
- **No cloud dependencies**: All processing happens locally
- **Your keys, your data**: You control all API credentials
- **Open source**: Audit every line of code

---

## 🚀 Why This Needs Claude (Anthropic OSS Application)

**Current limitation**: Using basic OpenAI GPT models with limited context and no multi-document reasoning.

### What Claude Would Unlock:

#### 1️⃣ **200K Context Window = True Workspace Intelligence**
- Analyze entire email threads + calendar history + document library simultaneously
- Example: *"Based on all my emails and meetings this month, what should I prioritize next week?"*

#### 2️⃣ **Constitutional AI = Safer Automation**
- Claude's built-in safety for sensitive operations (deleting emails, sharing docs)
- More reliable intent classification ("Is this a request to DELETE or DRAFT?")

#### 3️⃣ **Superior Document Understanding**
- Current: Basic text extraction from PDFs
- With Claude: Multi-document synthesis, cross-referencing, fact-checking
- Example: *"Compare this contract.pdf with our standard template and flag differences"*

#### 4️⃣ **Proactive Assistant (Not Just Reactive)**
- Daily briefings: "Here's what needs attention based on your emails, calendar, and tasks"
- Auto-categorize emails and suggest draft replies
- Predict scheduling conflicts before they happen

#### 5️⃣ **Privacy + Power = Anthropic's Vision**
This project embodies Anthropic's values:
- Self-hosted (no data monetization)
- Open source (community-auditable)
- Helpful, harmless, honest (Constitutional AI principles)
- Real-world utility (not just demos)

---

## 📸 Demo

### Email Management
![Email Demo](screenshots/email-demo.gif)

### Calendar Scheduling
![Calendar Demo](screenshots/calendar-demo.gif)

### Document Processing
![Docs Demo](screenshots/docs-demo.gif)

---

## 🏗️ Architecture
┌─────────────────────────────────────────┐
│ Telegram Interface │
│ (Natural Language Commands) │
└──────────────┬──────────────────────────┘
│
┌──────▼──────┐
│ Cleo Brain │ ← Main orchestrator
│ (n8n Core) │
└──────┬──────┘
│
┌─────────┴─────────┐
│ │
┌────▼────┐ ┌───▼────┐
│ AI Layer│ │ Memory │
│ (Claude)│◄────────┤Pipeline│
└────┬────┘ └────────┘
│
└─────┬─────┬─────┬─────┬─────┬──────┐
│ │ │ │ │ │
┌──▼─┐ ┌─▼──┐┌─▼──┐┌─▼──┐┌─▼───┐┌─▼───┐
│📧 │ │📅 ││📊 ││📝 ││☁️ ││✅ │
│Gmail│ │Cal ││Shts││Docs││Drive││Tasks│
└────┘ └────┘└────┘└────┘└─────┘└─────┘

text


**Why n8n + Claude is the Perfect Stack:**
- n8n: Visual workflow automation (no-code AI orchestration)
- Claude: Context-aware reasoning with safety guarantees
- Telegram: Universal interface (works on any device)
- Self-hosted: Complete data sovereignty

---

## 🛠️ Installation

### Quick Start (5 minutes)
```bash
# 1. Clone repo
git clone https://github.com/yourusername/cleo-ai-assistant
cd cleo-ai-assistant

# 2. Start n8n with Docker
docker-compose up -d

# 3. Import workflows
# Open http://localhost:5678
# Import all .json files from /workflows

# 4. Configure credentials (see setup guide)
📚 Full setup guide: docs/SETUP.md

🎓 Use Cases
For Developers
"Log this bug to my project tracker spreadsheet"
"Schedule code review with the team next Tuesday"
"Search my Drive for the API documentation"
For Founders
"What meetings do I have this week?"
"Draft an email to investors with Q4 metrics from the revenue sheet"
"Remind me to follow up with leads who haven't responded"
For Students
"Upload these lecture notes to Drive and summarize them"
"Add 'Study for exam' to my task list for Friday"
"When's my next free 2-hour block for project work?"
For Everyone
"What's on my calendar tomorrow?"
"Send an email to mom saying I'll call her tonight"
"Note: The wifi password is abc123"
🗺️ Roadmap
 Multi-agent architecture with 8 specialized agents
 Natural language processing for common tasks
 Persistent memory across conversations
 Smart reminder system
 Claude integration ← BLOCKED: Need Anthropic OSS Grant 🚨
 Voice message transcription + processing
 Multi-user support (family/team accounts)
 Slack/Discord adapters
 Mobile app (React Native wrapper)
🤝 Contributing
This started as my personal productivity stack — now it's open source!

Ways to contribute:

🐛 Report bugs
💡 Suggest features (Discussions)
🔧 Submit PRs (especially Claude integration once I get API access!)
⭐ Star the repo to show Anthropic there's demand
📊 Why Open Source?
I built Cleo because I was frustrated with:

Privacy concerns of cloud AI assistants
Fragmented apps (email, calendar, notes, tasks all separate)
No control over AI behavior and data usage
Open sourcing because:

Everyone deserves a private AI assistant
Community can add integrations I'd never think of
Transparency builds trust (especially for AI + personal data)
🎯 Applying for Anthropic's Open Source Program
This project is exactly what Claude is built for:

Large context windows (email threads + docs + calendar history)
Safety-critical operations (editing/deleting user data)
Multi-document reasoning (cross-referencing files)
Privacy-first (self-hosted, no middlemen)
Without Claude API access, I can't:

Build the proactive briefing system
Implement multi-document synthesis
Add constitutional safety guardrails
Scale context beyond GPT's 8K limit
If you think this deserves Claude access, star this repo! ⭐
It helps show Anthropic there's real demand.

📄 License
MIT © 2025 Matrix Workflows

Free to use, modify, distribute. Just don't claim you built it. 😊

🔗 Links
Documentation: Full setup guide 
Issues: Report bugs
Discussions: Feature requests
Built with ❤️ and n8n
Powered by: n8n | Telegram Bot API | Google Workspace APIs

🙏 Acknowledgments
n8n team for the amazing workflow platform
Anthropic for building Claude (hopefully soon in Cleo!)
Open source community for inspiration
Want to see Cleo powered by Claude?
Help me get approved → Star this repo ⭐
