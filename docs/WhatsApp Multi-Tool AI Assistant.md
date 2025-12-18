# WhatsApp Multi-Tool AI Assistant with GPT-4, Reminders & Multimedia

**Author:** Maxwell Melo
**Contact:** maxwell.melo0@gmail.com | WhatsApp: +55 86 99409-3040

---

## Description

Transform your WhatsApp into a powerful AI-powered personal assistant. This comprehensive n8n workflow combines GPT-4's conversational intelligence with multi-modal capabilities, allowing you to interact via text, images, audio, and documents. The assistant can manage your reminders, contacts, calendar, and emails—all through natural conversation.

### Who Is This For?

- **Entrepreneurs** who need a 24/7 virtual assistant
- **Professionals** managing busy schedules and communications
- **Power users** wanting a private, self-hosted AI solution
- **Developers** looking for a customizable automation foundation

### Core Capabilities

#### Multi-Modal Message Processing
- **Text**: Natural language conversation with GPT-4o
- **Images**: Visual analysis using GPT-4 Vision
- **Audio**: Voice message transcription with OpenAI Whisper
- **Documents**: PDF and document analysis with Google Gemini
- **Contacts**: Automatic vCard extraction and storage

#### Intelligent Agent Features
- Context-aware conversations with 10-message memory
- Tool integration: calculator, web browsing, reasoning
- Timezone-aware date and time operations
- Autonomous task delegation to specialist sub-workflows

#### Productivity Tools
- **Reminder System**: Create, update, and manage scheduled reminders
- **Contact Management**: Store and search your contacts
- **Calendar Integration**: Schedule events via Google Calendar
- **Email Management**: Send and manage emails via Gmail

#### Media Generation
- Generate images with DALL-E
- Create audio responses with Text-to-Speech
- Generate PDF documents from text

---

## Prerequisites

### Self-Hosted Requirement
This workflow requires a **self-hosted n8n instance** for full functionality. Some features may be limited on n8n Cloud.

### Required Services
- OpenAI API account (GPT-4, Whisper, TTS, DALL-E)
- Google Cloud account (Gemini API, Drive API)
- Redis server (for conversation memory)
- WhatsApp Business API or third-party integration (Evolution API/Wuzapi)

### Companion Workflows (Optional)
- Google Calendar AI Agent Template
- Gmail AI Agent Template
- Custom Web Search Agent

---

## Setup Instructions

### Step 1: Import the Workflow
1. Download the JSON file
2. In n8n, go to **Settings** → **Import Workflow**
3. Upload the JSON file

### Step 2: Configure Credentials
Create and configure these credentials in n8n:

| Credential | Service | Required For |
|------------|---------|--------------|
| OpenAI API | OpenAI | GPT-4, Whisper, TTS, DALL-E |
| Google Gemini | Google AI | Document/Image analysis |
| Redis | Redis Server | Conversation memory |
| Evolution API | WhatsApp | Message sending/receiving |
| Google Drive | Google | Document generation |

### Step 3: Replace Placeholders
Search the workflow for these placeholders and replace:
- `DEMO_*` - Credential IDs
- `SUA_*` - API keys
- `55XXXXXXXXXXX` - Your WhatsApp number

### Step 4: Create Data Tables
In n8n, create these Data Tables:

**Reminders Table:**
- `data_e_hora_lembrete` (datetime)
- `lembrete` (text)
- `contato` (text)
- `status` (text)

**Contacts Table:**
- `nome` (text)
- `whatsapp` (text)

### Step 5: Configure Sub-workflows
Import companion workflows and update the workflow call references.

### Step 6: Test
Send a test message to your WhatsApp number and verify the response.

---

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    WhatsApp Webhook                          │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Security Filters                                │
│  • Authorized Sender Check                                   │
│  • Direct Messages Only (No Groups)                          │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Message Type Router                             │
│  ├→ Text Messages                                            │
│  ├→ Images → GPT-4 Vision Analysis                          │
│  ├→ Audio → Whisper Transcription                           │
│  ├→ Documents → Gemini Analysis                             │
│  └→ Contacts → vCard Extraction                             │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Context Management                              │
│  • Store Message in Redis                                    │
│  • Retrieve Conversation History                            │
│  • Conversation Memory (10 messages)                        │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              AI Agent Orchestrator (GPT-4o)                 │
│  Tools Available:                                            │
│  • Calculator        • Web Browser                          │
│  • Reasoning         • Date/Time                            │
│  • Calendar Agent    • Email Agent                          │
│  • Reminders         • Contacts                             │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Response Type Handler                           │
│  ├→ Text → Send directly                                    │
│  ├→ Image → DALL-E Generation                               │
│  ├→ Audio → TTS Generation                                  │
│  └→ Document → PDF Creation                                 │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              WhatsApp Message Sender                         │
└─────────────────────────────────────────────────────────────┘
```

---

## Customization Tips

### Change the AI Model
Edit the "GPT-4o Language Model" node to use a different model (e.g., GPT-4 Turbo, Claude).

### Adjust Conversation Memory
Modify the "Conversation Memory (Redis)" node to change:
- Context window size (default: 10 messages)
- Memory TTL (default: 48 hours)

### Add New Tools
Create new tool nodes and connect them to the AI Agent to extend capabilities.

### Modify System Prompt
Edit the AI Agent node's system message to customize the assistant's personality and behavior.

---

## Troubleshooting

### Messages Not Being Received
- Check webhook configuration
- Verify WhatsApp API credentials
- Ensure the webhook URL is publicly accessible

### AI Not Responding
- Check OpenAI API key validity
- Verify Redis connection
- Check for errors in the execution log

### Tools Not Working
- Verify sub-workflow configurations
- Check credential permissions
- Test each tool individually

---

## Support

Need help implementing or customizing this workflow?

**Email:** maxwell.melo0@gmail.com
**WhatsApp:** +55 86 99409-3040

### Services Offered
- Custom implementation
- Workflow customization
- n8n training and consulting
- System integration

---

*Created by Maxwell Melo - Automation Specialist*
