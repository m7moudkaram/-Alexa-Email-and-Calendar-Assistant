# Alexa — AI Email & Calendar Assistant

An n8n-based AI agent that manages email and calendar tasks on the user's behalf. Built as part of the **Digital Egypt Pioneers Initiative (DEPI)**.

## Description

Alexa is an intelligent, professional Email and Calendar Assistant powered by **Google Gemini** and orchestrated through **n8n**. It connects to Gmail, Google Calendar, and SerpAPI to read and search emails, send messages, check schedules, create events, and pull information from the web — all while following strict rules around confirmation, accuracy, and never fabricating data.

The workflow is triggered by an incoming chat message, processed by an AI Agent node (Alexa), backed by a chat model, short-term conversation memory, and a set of connected tools.

## How It Works

1. **Trigger** — A chat message comes in and starts the workflow.
2. **Agent (Alexa)** — The core AI Agent node interprets the user's request and decides which tool(s) to use, following its defined behavior rules.
3. **Chat Model** — Google Gemini powers the agent's reasoning and responses.
4. **Memory** — A simple memory module retains context from earlier in the conversation (e.g., preferred meeting duration, frequently used recipients).
5. **Tools** — The agent calls one or more of the following as needed:
   - **Gmail – Get All**: search/retrieve emails
   - **Gmail – Send Message**: send emails
   - **Google Calendar – Get All**: check existing events
   - **Google Calendar – Create Event**: schedule new events
   - **Google Search (SerpAPI)**: fetch external information not available in email/calendar

## Core Behavior Rules

- **Never guesses.** Ambiguous requests (e.g., "tomorrow afternoon") are clarified before any action is taken.
- **Draft vs. Send.** Emails are only drafted unless the user explicitly asks to send them.
- **Conflict checking.** The calendar is always checked before creating an event; conflicts are reported to the user.
- **No fabrication.** The agent never invents emails, events, dates, or search results, and never claims an action succeeded unless the corresponding tool call actually completed.
- **Clarify, don't assume.** Missing information (recipient, subject, event time, etc.) is always requested from the user.

## Tools & Integrations

| Tool | Purpose |
|---|---|
| n8n | Workflow orchestration |
| Google Gemini | Chat model / reasoning engine |
| Gmail API | Read and send emails |
| Google Calendar API | Read and create calendar events |
| SerpAPI | Web search for external information |

## Use Cases

- "Check my emails from John this week."
- "Do I have any meetings tomorrow?"
- "Schedule a call with the team on Thursday at 4 PM."
- "Draft an email to my professor about the deadline extension."
- "Search for the latest AI agent frameworks."

## Notes

This project focuses less on tool integration (which is straightforward) and more on **prompt design** — defining clear rules for when the agent acts, when it asks for clarification, and how it handles uncertainty or failure. The system prompt functions as the actual design document for the agent's judgment and behavior.

---
Built as part of DEPI (Digital Egypt Pioneers Initiative).
