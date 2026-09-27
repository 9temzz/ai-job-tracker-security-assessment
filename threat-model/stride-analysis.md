# STRIDE Threat Analysis

This document identifies potential security threats affecting the AI Job Application Tracker using the STRIDE threat-modelling framework.

STRIDE stands for:

- Spoofing
- Tampering
- Repudiation
- Information Disclosure
- Denial of Service
- Elevation of Privilege

## Initial Threats

| ID | Component | Threat | STRIDE Category | Potential Impact |
|---|---|---|---|---|
| T01 | Incoming Email | Attacker sends a spoofed email pretending to be a legitimate employer | Spoofing | Incorrect application data may be processed |
| T02 | Gemini Input | Malicious email contains instructions designed to manipulate the AI model | Tampering | Incorrect classification or application status |
| T03 | Google Sheets | Application records are modified without authorisation | Tampering | Loss of data integrity |
| T04 | n8n | Workflow actions cannot be traced due to insufficient logging | Repudiation | Difficult to investigate incidents |
| T05 | Email Log | Sensitive email information is exposed to an unauthorised user | Information Disclosure | Exposure of personal/job application data |
| T06 | Credentials | API keys, OAuth tokens or credentials are exposed | Information Disclosure | External services may be compromised |
| T07 | Email Trigger | Large volumes of emails overload the workflow | Denial of Service | Workflow becomes unavailable or delayed |
| T08 | Gemini API | Excessive requests exhaust API quotas | Denial of Service | AI extraction stops working |
| T09 | n8n Admin | Attacker gains administrative access to n8n | Elevation of Privilege | Full control over workflows and credentials |
| T10 | Docker Host | Host compromise exposes n8n and stored secrets | Elevation of Privilege | Entire system could be compromised |
