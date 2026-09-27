# AI Job Tracker Security Assessment
## Overview
This project performs a cybersecurity assessment and threat model of an AI-powered job application tracking system.
The original system automatically processes job-related emails using Gmail, n8n, Google Vertex AI / Gemini and Google Sheets. It extracts application information, detects application status changes, prevents duplicate records and flags uncertain cases for manual review.
The purpose of this security project is to identify potential threats, assess their risk and recommend appropriate security controls.

## System Components
The system contains the following major components:
- Gmail
- Gmail Trigger / OAuth authentication
- Self-hosted n8n running in Docker
- Duplicate email detection
- AI Information Extractor
- OpenAI Chat Model
- Job-related email classification
- Application matching logic
- Google Sheets `Applications` sheet
- Google Sheets `Email Log`
- Manual `Needs Review` workflow

## Security Objectives
The assessment focuses on protecting:
- Gmail and OAuth credentials
- n8n authentication and configuration
- AI/API credentials
- Email content
- Personal job application data
- Application records
- Email log records
- Workflow integrity
- AI-generated classifications and extracted data
- Application matching accuracy

## Existing Controls
The current workflow already includes several controls designed to improve reliability and reduce incorrect processing:
- Duplicate email detection prevents the same message from being processed repeatedly.
- Job-related classification filters irrelevant emails.
- Existing application matching reduces duplicate application records.
- A `Needs Review` path handles cases where an application cannot be matched confidently.
