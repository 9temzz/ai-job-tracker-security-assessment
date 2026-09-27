# Data Flows and Trust Boundaries

This document describes how data moves between the main components of the AI Job Application Tracker and identifies important trust boundaries.

## Data Flows

| Source | Destination | Data |
|---|---|---|
| External Email Sender | Gmail | Email subject, sender, body and other message content |
| Gmail / IMAP | n8n | Raw email data |
| n8n | Gemini / Vertex AI | Email content for classification and information extraction |
| Gemini / Vertex AI | n8n | Structured extracted application information |
| n8n | Google Sheets Email Log | Email metadata and extracted information |
| n8n | Google Sheets Applications | Application details and application status updates |
| User | n8n | Workflow configuration and administrative actions |
| Docker Host | n8n | Runtime environment and system resources |

## Trust Boundaries

### External Email Boundary

Emails originate outside the trusted system.

Incoming email content must therefore be treated as untrusted input.

Possible security concerns include:

- spoofed sender information
- malicious email content
- phishing
- prompt injection
- unexpected or malformed data

### Gmail to n8n Boundary

n8n retrieves email data using authenticated access to Gmail / IMAP.

Compromise of the authentication credentials could allow unauthorised access to email data.

### n8n to Gemini Boundary

Email content is sent from n8n to the AI model for classification and information extraction.

Because the email originated from an external source, the AI model may receive attacker-controlled input.

Model outputs should therefore not automatically be trusted.

### n8n to Google Sheets Boundary

n8n writes application and email information into Google Sheets.

Unauthorised modification of these records could affect the integrity of the job application tracker.

### Docker Host Boundary

The Docker host runs the self-hosted n8n instance.

Compromise of the host could expose workflows, credentials and application data.

## Security Assumptions

n8n is treated as the central processing component.

External email content is treated as untrusted.

External services such as Gmail, Gemini and Google Sheets are accessed through authenticated connections.

Sensitive credentials must not be stored in this public GitHub repository.
