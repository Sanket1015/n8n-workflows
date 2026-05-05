# n8n Workflows

A collection of automation workflows I've built with n8n (https://n8n.io).

## About

I'm Sanket, an automation freelancer based in Kolkata, India. I build workflows that save businesses and solopreneurs hours of manual work every week — lead qualification, content repurposing, document processing, and custom integrations.

Each workflow here is exported as JSON and can be imported directly into any n8n instance.

## Workflows

### 08_ai_lead_qualifier.json — AI Lead Qualifier

Receives inbound leads via webhook, classifies them as HOT/WARM/COLD using Claude API, enriches HOT and WARM leads with inferred company data, logs everything to Airtable, and sends a Telegram alert for hot leads.

**Setup required after import:** (1) Create your own Anthropic API, Airtable, and Telegram credentials and assign them in each node. (2) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

### 09_content_repurposing_engine.json — Content Repurposing Engine

Accepts a YouTube or blog URL via webhook, generates four content pieces (LinkedIn post, 5 tweets, email newsletter, AI image prompt) using Claude API, and saves everything to a Google Doc. Supports partial success — if one LLM call fails, the others still produce output.

**Setup required after import:** (1) Create your own Anthropic API and Google Docs OAuth credentials and assign them in each node. (2) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

## Contact

- Email: sanket.automates@gmail.com
- LinkedIn: coming soon