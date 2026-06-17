# M04 — Customer Support Auto-Responder

## Overview
Automatically classifies and responds to customer support requests submitted via a Tally form. Uses Claude AI to categorise tickets, draft personalised replies, and route based on confidence score. Low-confidence tickets are escalated to a human via email.

## Flow
```
Tally Webhook → Claude AI (classify + draft) → Text Parser → JSON Parse
→ Router
  ├── Billing (score ≥ 0.75)   → Gmail Auto-Reply → Sheets + Notion
  ├── Technical (score ≥ 0.75) → Gmail Auto-Reply → Sheets + Notion
  ├── General (score ≥ 0.75)   → Gmail Auto-Reply → Sheets + Notion
  └── Escalation (score < 0.75) → Gmail Alert → Sheets + Notion
```

## Modules
- **Trigger:** Webhooks – Custom Webhook (Tally form)
- **AI:** Anthropic Claude – Simple Text Prompt (claude-sonnet-4-5)
- **Parser:** Text Parser – Match Pattern (regex JSON extraction)
- **Parse:** JSON – Parse JSON
- **Router:** Flow Control – Router (4 routes)
- **Email:** Gmail – Send an Email (×4)
- **Logging:** Google Sheets – Add a Row (×4)
- **Logging:** Notion – Create a Database Item (×4)

## Key Decisions
- Numeric confidence score (0.0–1.0) with 0.75 threshold for escalation
- Text Parser regex `\{[\s\S]*\}` with Singleline=Yes to strip Claude markdown fences
- Router filters use "Contains" operator (not "Equal to") for category matching
- Notion data source: Support Tickets DB under Make Automation Projects page
- Dual logging on all routes including escalation

## Lessons Learned
- Claude markdown fence stripping: Text Parser more reliable than replace() formula
- Router filter variables must be mapped from JSON module (not typed manually)
- Notion database fields exposed only after creating a data structure in JSON module
- Tally dropdown returns UUID in valueArray — Claude infers category from options text

## Stack
- Make.com (Tokens — no API key)
- Anthropic Claude Sonnet 4.5
- Tally (webhook trigger)
- Gmail
- Google Sheets — Cognflow Support Tracker
- Notion — Support Tickets (under Make Automation Projects)

## Status
✅ Complete — June 2026