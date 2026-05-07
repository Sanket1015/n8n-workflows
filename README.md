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

### 10_invoice_processor.json — Invoice/Receipt Processor

Watches a Gmail inbox for emails with PDF invoice attachments, extracts structured data (vendor, date, total, line items) using Claude's document understanding API, validates the extraction, and logs everything to a Google Sheet. Failed extractions trigger a Telegram alert so nothing gets silently dropped.

**Setup required after import:** (1) Create your own Anthropic API, Gmail OAuth, Google Sheets OAuth, and Telegram credentials and assign them in each node. (2) Create a Gmail label for invoices and update the Gmail Trigger node with your label ID. (3) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

### 11_invoice_daily_summary.json — Invoice Daily Summary

Companion workflow for the Invoice Processor. Runs daily at 6 PM, reads the Invoice Log Google Sheet, aggregates invoices from the last 24 hours (count, total amount, vendor list), and sends a Telegram summary. Sends a "no invoices" message if the period was empty rather than failing silently.

**Setup required after import:** (1) Create your own Google Sheets OAuth and Telegram credentials and assign them in each node. (2) Point the Google Sheets node to your own Invoice Log spreadsheet. (3) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

## Contact

- Email: sanket.automates@gmail.com
- LinkedIn: coming soon