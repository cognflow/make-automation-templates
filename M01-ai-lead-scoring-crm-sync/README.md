# M01 — AI Lead Scoring & CRM Sync

## Overview
Automatically scores inbound leads using Claude AI and syncs enriched records to Airtable CRM.

## Flow
Tally Form -> Make Webhook -> Claude AI -> Text Parser -> Airtable CRM

## Modules
1. Webhooks (Custom Webhook) - Receives Tally form submissions
2. HTTP (Make a Request) - Calls Claude API for lead scoring
3. Text Parser x6 - Extracts Score, Tier, Qualified, Intent, Suggested Service, Reasoning
4. Airtable (Create a Record) - Writes enriched lead to CRM

## AI Output Fields
- Score: 0-100
- Tier: Hot / Warm / Cold
- Qualified: true / false
- Intent: One sentence summary
- Suggested Service: Recommended Cognflow service
- AI Reasoning: Explanation of score

## Tools
- Make
- Claude claude-sonnet-4-5
- Airtable
- Tally Forms
