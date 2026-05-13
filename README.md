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

### 12_dental_appointment_reminder.json — Dental Appointment Reminder

Part 1 of the Dental Clinic Automation Suite. Runs daily at 9 AM, reads a patient database from Google Sheets, filters for tomorrow's appointments (Status = Scheduled, has email, no reminder already sent), attaches clinic config, and sends a personalized reminder email. Updates a tracking column to prevent duplicate sends on re-runs.

**Setup required after import:** (1) Create your own Gmail OAuth and Google Sheets OAuth credentials and assign them in each node. (2) Create your own Google Sheet with a "Patients" tab and a "Clinic Config" tab matching the expected column names. (3) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

### 13_dental_review_request.json — Dental Post-Visit Review Request

Part 2 of the Dental Clinic Automation Suite. Runs daily at 6 PM, finds patients who completed their visit today and haven't received a review request yet, and sends a thank-you email with a direct Google review link from the clinic config. Updates a tracking column to prevent duplicates.

**Setup required after import:** (1) Same credentials as Workflow 12. (2) Same Google Sheet structure. (3) Add your clinic's Google review URL to the Clinic Config tab. (4) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

### 14_dental_noshow_reengagement.json — Dental No-Show Re-engagement

Part 3 of the Dental Clinic Automation Suite. Runs daily at 10 AM, finds patients who missed their appointment yesterday (Status = No-Show) and haven't been contacted yet, and sends a friendly, no-guilt rebooking email with the clinic's phone number. Updates a tracking column to prevent duplicates.

**Setup required after import:** (1) Same credentials as Workflow 12. (2) Same Google Sheet structure. (3) Create or assign your own error handler workflow in Workflow Settings → Error Workflow.

## Contact

- Email: sanket.automates@gmail.com
- LinkedIn: coming soon