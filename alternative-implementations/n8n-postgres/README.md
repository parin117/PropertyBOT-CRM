# Property Search Automation (n8n + PostgreSQL)

## Overview

This implementation is an improved version of the original n8n + Google Sheets prototype.

The objective was to migrate property inventory management and search operations from spreadsheets to a relational database while preserving the conversational WhatsApp experience.

This version was developed as an alternative implementation alongside the OpenClaw architecture during the development of Yandox Property CRM.

---

## Architecture

WhatsApp User
      │
      ▼
WhatsApp Cloud API
      │
      ▼
n8n Workflow
      │
      ├── Duplicate Prevention
      │
      ├── Regex / Entity Extraction
      │
      ├── Session Management
      │
      ├── PostgreSQL Queries
      │
      ├── Property Matching
      │
      └── WhatsApp Response

                        │
                        ▼

                 PostgreSQL
                 Property DB

---

## Features

### WhatsApp-Based Property Search

Users interact naturally through WhatsApp.

Examples:

- Flat in Gota under 80 lakh
- Villa above 150 lakh
- Plot in Ahmedabad

---

### Structured Database Search

Property inventory is stored in PostgreSQL.

Benefits include:

- Faster search
- Better filtering
- Relational data support
- Improved scalability

---

### Dynamic SQL-Based Filtering

Searches can be filtered using:

- Location
- Property Type
- Budget
- Size
- Bedrooms

depending on information provided by the user.

---

### Session Tracking

The workflow maintains user search context throughout the conversation.

This allows users to provide information incrementally.

Example:

User:
Gota

User:
Flat

User:
Under 80 lakh

The workflow combines all requirements before searching.

---

### Human Agent Handoff

Users may request:

Agent

to escalate the conversation to a property consultant.

---

### Duplicate Event Protection

Meta webhook retries are detected and ignored to prevent duplicate processing.

---

## Technology Stack

- n8n
- PostgreSQL
- WhatsApp Cloud API
- JavaScript Code Nodes
- Ollama (optional extraction layer)

---

## Improvements Over Google Sheets Version

| Area | Google Sheets | PostgreSQL |
|--------|--------|--------|
| Query Performance | Limited | Fast |
| Scalability | Low | High |
| Data Integrity | Basic | Strong |
| Filtering | Spreadsheet Logic | SQL Queries |
| Inventory Management | Manual | Structured |

---

## Role Within Yandox Property CRM

This implementation served as an intermediate architecture between the initial Google Sheets prototype and the final production-grade OpenClaw platform.

Lessons learned from this version influenced:

- Database schema design
- Property search logic
- Session management strategy
- WhatsApp interaction flow

---

## Relationship to OpenClaw

This workflow is not the production implementation.

The final Yandox Property CRM architecture uses:

- Node.js
- Express
- PostgreSQL
- Redis
- BullMQ
- OpenClaw
- Ollama

to provide a scalable and fault-tolerant AI-powered property search platform.

This n8n implementation remains as an alternative prototype and architectural reference.

---

## Project Evolution

Phase 1
n8n + Google Sheets

↓

Phase 2
n8n + PostgreSQL

↓

Phase 3
OpenClaw + BullMQ + Redis + PostgreSQL

↓

Production
Yandox Property CRM

---

## Historical Context

The n8n PostgreSQL workflow was developed in parallel with the OpenClaw implementation as part of the broader Yandox Property CRM initiative. It demonstrates an alternative low-code approach for property search automation while sharing the same business objective and conversation flow as the production system.
