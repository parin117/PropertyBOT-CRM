# Property Search Automation (n8n + Google Sheets)

## Overview

This implementation is an early prototype of the Yandox Property CRM WhatsApp automation system.

The goal was to validate whether property requirements could be collected conversationally through WhatsApp and matched against an inventory database using low-code workflow automation.

This version uses Google Sheets as both:

- Property inventory source
- User session storage

The workflow was developed in parallel with the OpenClaw implementation during the early experimentation phase of the project.

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
      ├── Entity Extraction (Ollama)
      │
      ├── Session Retrieval
      │
      │      Google Sheets
      │
      ├── Context Merge
      │
      ├── Property Filtering
      │
      └── WhatsApp Response

---

## Features

### WhatsApp Conversation Interface

Users can search properties using natural language.

Examples:

- Flat in Ahmedabad under 80 lakh
- Villa in Gota above 120 lakh
- Plot near SG Highway

---

### AI-Based Entity Extraction

Uses Ollama LLM to extract:

- Location
- Property Type
- Budget
- Size
- Bedrooms

from free-form user messages.

---

### Session Memory

Conversation context is stored in Google Sheets.

The workflow remembers:

- Location
- Budget
- Property Type
- Size constraints
- Bedroom preferences

across multiple messages.

---

### Property Search

Properties are filtered from a Google Sheets inventory dataset based on extracted user requirements.

---

### Agent Escalation

Users can request:

Agent

to be handed off to a human property consultant.

---

### Duplicate Message Prevention

Webhook retry protection prevents duplicate WhatsApp events from being processed multiple times.

---

## Technology Stack

- n8n
- WhatsApp Cloud API
- Ollama
- Google Sheets
- JavaScript Code Nodes

---

## Limitations

This implementation was created as a proof-of-concept.

Known limitations:

- Google Sheets is not suitable for large inventories
- Limited query performance
- Spreadsheet-based session storage
- Difficult to scale beyond prototype workloads

---

## Evolution

This implementation was later enhanced by replacing Google Sheets with PostgreSQL to improve scalability and search performance.

See:

../n8n-postgres/

---

## Purpose in Project History

This workflow represents the initial validation phase of the Yandox Property CRM property-search automation system and helped establish the conversation flow and property matching logic later used in production-oriented implementations.
