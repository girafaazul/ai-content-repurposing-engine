# AI Content Repurposing Engine
### Automated multi-platform content distribution powered by Claude AI + n8n

---

## Overview

This pipeline monitors any RSS feed for new content, automatically cleans and extracts the article, repurposes it into platform-native formats for LinkedIn, Twitter/X, and email newsletter using Claude AI, and saves all outputs to a Google Sheets content queue — ready to publish or schedule.

Built for content marketers, agencies, and solo creators who publish consistently across multiple channels without a dedicated team.

---

## The Problem It Solves

Creating platform-native content for LinkedIn, Twitter/X, and email from a single article takes 2–3 hours manually. Most teams either skip distribution or publish the same copy everywhere — which kills engagement.

This pipeline handles the entire repurposing workflow in **under 60 seconds per article**, automatically, every time new content is published.

---

## How It Works

```
RSS Feed (polled every hour)
        ↓
Content Validation (title required)
        ↓
HTML Cleaner + Text Extractor
        ↓
Claude AI — Repurpose for 3 Platforms simultaneously
        ↓
Output Structurer (LinkedIn / Twitter / Email fields)
        ↓
Parse Validation (error routing)
        ↓
Google Sheets — Content Queue (ready to publish)
        ↓
Google Sheets — Error Log (failed items for review)
```

---

## What Gets Generated Per Article

### LinkedIn Post
- Hook line (attention-grabbing opener)
- Body (3–5 short paragraphs, professional tone)
- Call to action
- 5 relevant hashtags
- Full formatted post ready to copy-paste

### Twitter/X Thread
- 5-tweet thread
- Tweet 1: hook
- Tweets 2–4: key insights
- Tweet 5: CTA + original article link

### Email Newsletter
- Subject line (max 60 chars, optimized for open rate)
- Preview text (max 90 chars)
- Full email body (conversational tone, 3–4 paragraphs)
- CTA button text + URL

---

## Tech Stack

| Tool | Role |
|---|---|
| **n8n** | Workflow orchestration + RSS polling |
| **Claude API (Anthropic)** | Content repurposing engine |
| **Google Sheets API** | Content queue + error log |
| **RSS Feed** | Content source trigger |

---

## Workflow Architecture

![AI Content Repurposing Engine](./workflow-screenshot.png)

> 8-node workflow with RSS polling, HTML cleaning, parallel platform repurposing via Claude AI, parse validation, and dual-destination output routing.

---

## Output Structure (Google Sheets Columns)

| Column | Description |
|---|---|
| `original_title` | Article title from RSS |
| `original_url` | Source article URL |
| `original_author` | Author name |
| `published_at` | Original publish date |
| `word_count` | Source article word count |
| `linkedin_hook` | LinkedIn opening line |
| `linkedin_body` | LinkedIn post body |
| `linkedin_hashtags` | 5 hashtags |
| `linkedin_full_post` | Complete formatted post |
| `twitter_thread` | Full 5-tweet thread |
| `email_subject` | Email subject line |
| `email_preview` | Email preview text |
| `email_body` | Full email body |
| `email_cta_text` | CTA button label |
| `article_summary` | 2-sentence article summary |
| `processed_at` | Pipeline execution timestamp |

---

## Example Output

**Input:** Article titled *"5 Ways AI Is Changing B2B Sales in 2026"*

**LinkedIn Hook generated:**
> "AI just made your SDR team 10x more efficient. Here's what that actually looks like in practice."

**Twitter Thread Tweet 1:**
> "AI is reshaping B2B sales faster than most teams realize. Here are 5 changes happening right now — and what to do about each one 🧵"

**Email Subject:**
> "The AI shift your sales team can't ignore"

---

## Use Cases

- **Marketing agencies** — repurpose client blog content across all channels automatically
- **B2B SaaS companies** — distribute thought leadership content without extra headcount
- **Solo creators** — maintain consistent presence on LinkedIn + Twitter + email with one workflow
- **Media companies** — build content queues from RSS feeds at scale

---

## Setup

1. Import `ai-content-repurposing-engine.json` into your n8n instance
2. Set your **RSS Feed URL** in the trigger node
3. Add your **Anthropic API key** as an HTTP Header Auth credential
4. Connect your **Google Sheets** credential and set your Sheet ID
5. Activate the workflow — it polls automatically every hour

---

## Customization

- **Polling frequency:** change from hourly to every 15 min, daily, or on-demand
- **Platforms:** extend the Claude prompt to add Instagram captions, YouTube descriptions, or blog meta tags
- **Tone:** adjust the platform tone in the Claude prompt (formal, casual, bold, educational)
- **Thread length:** increase or decrease Twitter thread tweets in the prompt
- **Publishing:** connect Buffer, Hootsuite, or Beehiiv nodes to publish directly instead of saving to Sheets

---

## About

Built by a freelance AI Automation Engineer specializing in n8n workflows, Claude API integrations, and content operations automation.

Open to custom implementations — [contact via Upwork](#)
