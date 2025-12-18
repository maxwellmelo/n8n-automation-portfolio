# WhatsApp Financial Analysis Assistant with SQL Database & GPT-4o

**Author:** Maxwell Melo
**Contact:** maxwell.melo0@gmail.com | WhatsApp: +55 86 99409-3040

---

## Description

Transform your financial operations with this intelligent WhatsApp assistant powered by GPT-4o and connected directly to your SQL database. This template enables natural language queries against financial data, providing instant insights, reports, and analysis through simple WhatsApp conversations.

### Who Is This For?

- **Financial managers** who need quick access to financial data on-the-go
- **CFOs and executives** wanting instant financial summaries
- **Accountants** analyzing receivables, payables, and cash flow
- **Business owners** monitoring financial health via WhatsApp
- **IT teams** building conversational interfaces for ERP systems

### Core Features

#### Multi-Modal Message Processing
- **Text**: Natural language financial queries
- **Audio**: Voice message transcription with OpenAI Whisper
- **Images**: Document and chart analysis with GPT-4 Vision

#### SQL Database Integration
- Direct connection to Microsoft SQL Server
- Pre-configured financial queries (receivables, payables, aging reports)
- Support for custom SQL queries via AI
- Compatible with TOTVS RM and similar ERP systems

#### AI-Powered Financial Analysis
- **GPT-4o** for intelligent query understanding
- Built-in **Calculator** tool for complex calculations
- **Think/Reasoning** tool for multi-step analysis
- Context-aware responses with conversation memory

---

## Prerequisites

### Self-Hosted Requirement
This workflow requires a **self-hosted n8n instance** for full functionality.

### Community Nodes Required
This template uses community nodes that must be installed:
- `n8n-nodes-evolution-api` - WhatsApp Evolution API integration
- `@n8n/n8n-nodes-langchain` - AI/LangChain nodes (built-in)

### Required Services
| Service | Purpose |
|---------|---------|
| OpenAI API | GPT-4o, Whisper, Vision |
| Redis | Conversation memory |
| Microsoft SQL Server | Financial database |
| Evolution API | WhatsApp integration |

---

## Setup Instructions

### Step 1: Install Community Nodes
In n8n, go to **Settings** → **Community Nodes** and install:
```
n8n-nodes-evolution-api
```

### Step 2: Import and Configure
1. Import the workflow JSON
2. Configure credentials for all services
3. Replace placeholder values (`DEMO_*`, `SUA_*`)
4. Add your authorized WhatsApp numbers
5. Customize SQL queries for your database schema

### Step 3: Test
Send a test message like "Show me receivables summary" to verify the setup.

---

## Node Reference

| Node Name | Type | Purpose |
|-----------|------|---------|
| WhatsApp Webhook Receiver | Webhook | Receives incoming messages |
| Configuration Settings | Set | Stores configuration values |
| Filter Own Messages | If | Ignores bot's own messages |
| Filter Authorized Numbers | If | Security filter for users |
| Route By Message Type | Switch | Routes text/audio/image |
| Whisper Audio Transcription | OpenAI | Transcribes voice messages |
| GPT-4 Vision Image Analysis | OpenAI | Analyzes images |
| Redis Conversation Memory | Memory | Stores chat context |
| Financial AI Agent | AI Agent | Main intelligence |
| SQL Query Tool | Tool | Executes database queries |
| Calculator Tool | Tool | Mathematical operations |
| Reasoning Tool | Tool | Complex analysis |
| Send Text via WhatsApp | Evolution API | Sends responses |

---

## Example Queries

- "What's our receivables summary?"
- "Show me overdue invoices over $10,000"
- "Who are our top debtors?"
- "Compare revenue: this month vs last month"
- "What's the aging report for accounts payable?"

---

## Support

**Email:** maxwell.melo0@gmail.com
**WhatsApp:** +55 86 99409-3040

### Services Offered
- Custom implementation
- Database integration
- AI prompt engineering
- n8n training

---

*Created by Maxwell Melo - Automation Specialist*
