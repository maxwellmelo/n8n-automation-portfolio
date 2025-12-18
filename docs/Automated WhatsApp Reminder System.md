# Automated WhatsApp Reminder System with Scheduled Delivery & Number Normalization

**Author:** Maxwell Melo
**Contact:** maxwell.melo0@gmail.com | WhatsApp: +55 86 99409-3040

---

## Description

Transform your workflow with this powerful automated reminder system that delivers WhatsApp messages precisely when you need them. This template provides a complete solution for scheduling and sending reminders through WhatsApp, with intelligent phone number normalization that handles various Brazilian phone formats.

### Who Is This For?

- **Business owners** who need to send appointment reminders to clients
- **Healthcare providers** managing patient appointment notifications
- **Service companies** automating follow-up communications
- **Personal users** wanting automated reminders via WhatsApp
- **Developers** building notification systems

### Core Features

#### Scheduled Delivery System
- Minute-by-minute polling for pending reminders
- Precise delivery timing based on scheduled datetime
- UTC timezone normalization for accurate scheduling
- Support for both internal and external recipients

#### Smart Phone Number Normalization
- Automatic handling of Brazilian phone formats (DDI + DDD)
- Removes 9th digit when needed for WhatsApp compatibility
- Supports various input formats (with/without country code)
- Validates and formats numbers to WhatsApp API requirements

#### Database Integration
- Uses n8n Data Tables for reminder storage
- Tracks reminder status (PENDING/SENT)
- Supports custom fields: datetime, message, contact, status
- Automatic status updates after successful delivery

#### Error Handling
- Built-in error trigger for workflow failures
- WhatsApp notification when errors occur
- Detailed error messages for debugging

---

## Prerequisites

### Self-Hosted Requirement
This workflow requires a **self-hosted n8n instance** for full functionality due to Evolution API integration.

### Required Services
- Evolution API or similar WhatsApp Business API
- n8n Data Tables (built-in)
- Self-hosted n8n instance

### Data Table Structure
Create a Data Table named "reminders" with columns:
| Column | Type | Description |
|--------|------|-------------|
| data_e_hora_lembrete | datetime | Scheduled datetime for reminder |
| lembrete | text | The reminder message content |
| contato | text | Phone number of recipient |
| status | text | PENDING or SENT |

---

## Setup Instructions

### Step 1: Import the Workflow
1. Download this JSON file
2. In n8n, go to **Settings** → **Import Workflow**
3. Upload the JSON file

### Step 2: Configure Credentials
Create Evolution API credentials in n8n with your:
- API URL
- API Key
- Instance name

### Step 3: Create Data Table
Create a Data Table with the structure described above.

### Step 4: Replace Placeholders
Search the workflow for these placeholders and replace:
- `DEMO_*` - Credential and table IDs
- `SuaInstancia` - Your Evolution API instance name
- `55XXXXXXXXXXX` - Your WhatsApp number for error notifications

### Step 5: Activate & Test
Enable the workflow and add a test reminder to verify functionality.

---

## Workflow Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              Scheduled Check (Every Minute)                  │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Get Pending Reminders (status=PENDING)          │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Extract Reminder Data Fields                    │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Normalize DateTime to UTC                       │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Check If Reminder Is Due                        │
│              (scheduled_time <= current_time)                │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│              Route By Recipient Type                         │
│              ├→ Internal (specific number)                   │
│              └→ External (other contacts)                    │
└───────────┬─────────────────────────────────────┬───────────┘
            │                                     │
┌───────────▼───────────────┐       ┌────────────▼────────────┐
│ Normalize Phone (Internal)│       │ Normalize Phone (External)│
└───────────┬───────────────┘       └────────────┬────────────┘
            │                                     │
┌───────────▼───────────────┐       ┌────────────▼────────────┐
│ Send WhatsApp (Internal)  │       │ Send WhatsApp (External)  │
└───────────┬───────────────┘       └────────────┬────────────┘
            │                                     │
┌───────────▼───────────────┐       ┌────────────▼────────────┐
│ Update Status (Internal)  │       │ Update Status (External)  │
└───────────────────────────┘       └─────────────────────────┘
```

---

## Node Descriptions

| Node Name | Type | Purpose |
|-----------|------|---------|
| Scheduled Check (Every Minute) | Schedule Trigger | Polls every minute for pending reminders |
| Get Pending Reminders from Database | Data Table | Fetches reminders with status=PENDING |
| Extract Reminder Data Fields | Set | Maps fields for processing |
| Normalize DateTime to UTC | Code | Converts datetime to UTC for comparison |
| Check If Reminder Is Due | If | Compares scheduled time with current time |
| Route By Recipient Type | If | Splits flow for internal vs external contacts |
| Normalize Phone Number | Code | Formats phone numbers for WhatsApp API |
| Send WhatsApp Reminder | Evolution API | Sends the reminder message |
| Update Status to SENT | Data Table | Updates reminder status after sending |
| Error Handler Trigger | Error Trigger | Catches workflow errors |
| Send Error Notification | Evolution API | Alerts admin of errors via WhatsApp |

---

## Customization Tips

### Change Polling Interval
Edit the "Scheduled Check (Every Minute)" node to modify how often pending reminders are checked.

### Add More Fields
Extend the Data Table and workflow to include additional fields like:
- Priority level
- Category/type
- Recurrence rules
- Delivery confirmation

### Multiple WhatsApp Instances
Duplicate the sender nodes and add logic to route messages to different WhatsApp instances based on criteria.

### Add Retry Logic
Implement retry mechanism for failed message deliveries.

---

## Troubleshooting

### Reminders Not Sending
- Check if the reminder datetime has passed (compare UTC times)
- Verify the status is "PENDING" in the Data Table
- Check Evolution API credentials and instance status
- Review execution logs for errors

### Phone Numbers Not Working
- Ensure numbers include country code (55 for Brazil)
- Check the normalization logic handles your number format
- Verify the WhatsApp number is registered

### Time Zone Issues
- The workflow converts all times to UTC for comparison
- Set your n8n instance timezone correctly in settings
- Store reminder times in your local timezone (conversion handled automatically)

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
