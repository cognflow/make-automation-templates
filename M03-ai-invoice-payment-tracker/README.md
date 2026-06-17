\# M03 — AI Invoice \& Payment Tracker



An AI-powered finance automation workflow built with Make.com for tracking invoices, monitoring payments, sending reminders, and maintaining operational visibility across invoice lifecycles.



\---



\# Overview



This automation streamlines invoice processing and payment management by combining AI-powered extraction, workflow automation, and centralized tracking.



The scenario helps reduce manual financial operations by automatically:



\* Capturing invoice information

\* Tracking payment status

\* Sending reminders

\* Logging transactions

\* Organizing records

\* Monitoring outstanding invoices



\---



\# Features



\## Automated Invoice Processing



\* Detects and processes incoming invoices

\* Extracts structured invoice data

\* Categorizes invoices automatically



\## Payment Tracking



\* Tracks paid, pending, and overdue invoices

\* Maintains centralized invoice records

\* Updates payment statuses automatically



\## AI-Powered Data Extraction



\* Uses AI to identify:



&#x20; \* Invoice number

&#x20; \* Vendor details

&#x20; \* Amounts

&#x20; \* Due dates

&#x20; \* Payment references



\## Notifications \& Alerts



\* Sends payment reminders

\* Triggers overdue alerts

\* Supports finance follow-up workflows



\## Reporting \& Visibility



\* Provides organized invoice monitoring

\* Simplifies bookkeeping operations

\* Supports operational finance workflows



\---



\# Tech Stack



\* Make.com

\* OpenAI

\* Gmail

\* Google Sheets



\---



\# Project Structure



```text

M03-ai-invoice-payment-tracker/

│

├── README.md

└── M03 - AI Invoice \& Payment Tracker.blueprint.json

```



\---



\# Setup Instructions



\## 1. Import Blueprint



Import the `.blueprint.json` file into Make.com.



\## 2. Configure Connections



Connect required services:



\* Gmail

\* Google Sheets

\* OpenAI



\## 3. Configure Variables



Update:



\* Spreadsheet IDs

\* Email settings

\* API keys

\* Folder references



\## 4. Test Workflow



Run the scenario manually to validate:

\# M03 — AI Invoice \& Payment Tracker



\*\*Cognflow Make.com Automation Portfolio\*\*



Automatically extracts invoice data from Gmail using Claude AI, logs it to Google Sheets and Notion, and sends payment reminder emails based on due date logic.



\---



\## Overview



| Property | Detail |

|---|---|

| Platform | Make.com |

| AI Model | Claude Sonnet 4.5 (Anthropic) |

| Trigger | Gmail — Watch Emails |

| Outputs | Google Sheets + Notion + Gmail Reminders |

| Use Case | Accounts payable automation for small businesses and agencies |



\---



\## Flow Architecture

Gmail (Watch Emails)



└── Gmail (Get an Email)



└── Anthropic Claude (Simple Text Prompt)



└── JSON (Parse JSON)



└── Google Sheets (Add a Row)



└── Notion (Create a Page)



└── Router



├── Route 1: Due in 7 days → Gmail (Send Reminder)



└── Route 2: Due Today → Gmail (Send Alert)

## Modules



| # | Module | App | Purpose |

|---|---|---|---|

| 1 | Watch Emails | Gmail | Trigger on new unread emails |

| 6 | Get an Email | Gmail | Fetch full email content by Message ID |

| 8 | Simple Text Prompt | Anthropic Claude | Extract invoice fields from email body |

| 9 | Parse JSON | JSON | Parse Claude's structured JSON output |

| 10 | Add a Row | Google Sheets | Log invoice data to tracker sheet |

| 11 | Create a Page | Notion | Create invoice record in Notion database |

| 13 | Router | Make | Branch on due date conditions |

| 14 | Send an Email | Gmail | "Payment Due Soon" reminder (≤7 days) |

| 15 | Send an Email | Gmail | "Payment Due Today" alert |



\---



\## Claude AI Prompt

Extract the following fields from this invoice email and return ONLY a raw JSON object.



Do not use markdown. Do not use code blocks. Do not add any explanation.



Start your response with { and end with }.

{



"vendor": "",



"invoice\_number": "",



"invoice\_date": "",



"due\_date": "",



"amount": "",



"currency": "",



"status": "unpaid"



}

Email content:



{{6.Full text body}}

---



\## Data Destinations



\### Google Sheets — Cognflow Invoice Tracker



| Column | Source |

|---|---|

| Invoice # | `9.invoice\_number` |

| Vendor | `9.vendor` |

| Amount | `9.amount` |

| Currency | `9.currency` |

| Invoice Date | `9.invoice\_date` |

| Due Date | `9.due\_date` |

| Status | `9.status` |

| Source | `Gmail` (static) |

| Logged At | `1.Date` |



\### Notion — Invoices Database



Schema: Invoice # (Title) · Vendor · Amount · Currency · Invoice Date · Due Date · Status · Source · Logged At



\---



\## Reminder Logic



| Route | Condition | Email Subject |

|---|---|---|

| Route 1 | `due\_date ≤ now + 7 days AND due\_date > now` | `Payment Due Soon: INV-XXX - Vendor` |

| Route 2 | `due\_date = today` | `PAYMENT DUE TODAY: INV-XXX - Vendor` |



\---



\## Setup Instructions



\### Prerequisites

\- Make.com account

\- Gmail account (for trigger and sending)

\- Google Sheets spreadsheet: `Cognflow Invoice Tracker`

\- Notion database: `Invoices` (under Cognflow HQ)

\- Anthropic Claude app connected in Make



\### Connections Required

\- Gmail — OAuth connection

\- Google Sheets — OAuth connection

\- Notion — Internal Integration Token (`ntn\_...`)

\- Anthropic Claude — Make Tokens (no API key needed)



\---



\## Test Payload



Send an email to your connected Gmail with this body:

Invoice Number: INV-2025-042



Vendor: TechSoft Solutions



Invoice Date: 2026-06-01



Due Date: 2026-06-20



Amount: 2500.00



Currency: USD



Status: Unpaid

\*\*Note:\*\* Move emails from Spam to Inbox before running. Gmail Watch Emails only monitors Inbox.



\---



\## Known Limitations



\- Gmail trigger monitors Inbox only — invoice emails must not be in Spam

\- Claude may wrap JSON in markdown fences; use `replace()` in JSON string field to strip them

\- Notion title renders as literal text if invoice\_number is empty — use `ifempty(9.invoice\_number; "INV-UNKNOWN")` as fallback



\---



\## Portfolio Context



\*\*Cognflow\*\* is an AI business automation agency built on Make.com and n8n.

This is project \*\*M03\*\* of the Make.com automation portfolio.



| Project | Status |

|---|---|

| M01 — AI Lead Scoring \& CRM Sync | ✅ Complete |

| M02 — Social Media Content Engine | ✅ Complete |

| M03 — AI Invoice \& Payment Tracker | ✅ Complete |

| M04 — Customer Support Auto-Responder | 🔜 Next |



\---



\## Author



\*\*Igwe Ogaji Samuel\*\* — Cloud \& DevOps Engineer · AI Automation Specialist

\- GitHub: \[github.com/cognflow](https://github.com/cognflow)

\- LinkedIn: \[linkedin.com/in/igwe-ogaji](https://linkedin.com/in/igwe-ogaji)

