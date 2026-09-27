# Asset Inventory

This document identifies the main assets within the AI Job Application Tracker that require protection.

| Asset | Description | Sensitivity |
|---|---|---|
| Gmail / IMAP credentials | Credentials used to access incoming job-related emails | Critical |
| n8n account | Provides access to the automation workflows | Critical |
| Gemini / Vertex AI credentials | Credentials used to access the AI model | High |
| Google Sheets credentials | Credentials used to access job application data | Critical |
| Applications sheet | Stores companies, roles, statuses and application IDs | High |
| Email Log sheet | Stores information extracted from incoming emails | High |
| n8n workflow | Contains automation logic for processing application emails | High |
| Docker host | Runs the self-hosted n8n environment | Critical |
| AI prompts | Instructions used to classify and extract email information | Medium |
| Application IDs | Used to link emails with existing applications | Medium |
| Needs Review records | Stores emails that require manual checking | High |

## Security Objectives

The main security objectives are to protect the confidentiality, integrity and availability of these assets.

Confidentiality means sensitive information should only be accessible to authorised users.

Integrity means application records, emails and workflow logic should not be modified without authorisation.

Availability means the job tracking system should remain accessible and operational when required.
