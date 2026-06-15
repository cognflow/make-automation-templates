# M02 — Social Media Content Engine

## Overview
Automatically generates platform-specific social media captions using Claude AI, triggered by a new row added to a Google Sheets content brief.

## Flow
Google Sheets (Content Brief) -> Make Webhook -> Claude AI -> Text Parser x3 -> Google Sheets (Generated Drafts)

## Modules
1. Google Sheets (Watch New Rows) - Monitors Content Briefs tab for new entries
2. HTTP (Make a Request) - Calls Claude API for caption generation
3. Text Parser x3 - Extracts LinkedIn, Instagram, and Twitter/X captions
4. Google Sheets (Add a Row) - Writes generated captions to Generated Drafts tab

## AI Output Fields
- LinkedIn Caption: Professional caption with hashtags (max 150 words)
- Instagram Caption: Engaging caption with emojis and hashtags (max 100 words)
- Twitter/X Caption: Concise punchy caption with hashtags (max 280 characters)

## Google Sheets Schema
### Content Briefs (Trigger)
- Topic, Tone, CTA, Keywords, Status

### Generated Drafts (Output)
- Topic, LinkedIn Caption, Instagram Caption, Twitter/X Caption, Generated At

## Tools
- Make
- Claude claude-sonnet-4-5
- Google Sheets
