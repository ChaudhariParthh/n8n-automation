# n8n WhatsApp Calendar Assistant Workflow

<img width="1132" height="531" alt="whatsapp-appointment-workflow-using-twilio" src="https://github.com/user-attachments/assets/b8e16e36-a431-40ff-b4b6-81f09c13ee8a" />


## Project Overview

This project is an AI-powered WhatsApp Calendar Assistant created using:

* n8n
* Twilio WhatsApp Sandbox
* OpenAI Chat Model
* Google Calendar API

The workflow allows a user to send messages on WhatsApp and automatically receive AI-generated responses about meetings and appointments from Google Calendar.

---

# Main Objective

The objective of this workflow is:

* Receive a WhatsApp message from the user
* Understand the query using AI
* Check Google Calendar events
* Count meetings/events
* Send the response back on WhatsApp automatically

---

# Example User Queries

## Query 1

```text
How many meetings today?
```

## Query 2

```text
How many meetings tomorrow?
```

## Query 3

```text
How many meetings on 9th May 2026?
```

---

# Workflow Architecture

```text
Twilio Trigger
      ↓
AI Agent
  ↙        ↘
OpenAI    Google Calendar Tool
Chat Model
      ↓
Send SMS/MMS/WhatsApp Message
```

---

# Workflow Explanation

## Step 1 — User Sends WhatsApp Message

The user sends a WhatsApp message to the Twilio Sandbox number.

Example:

```text
How many meetings today?
```

Twilio receives the message and forwards it to the n8n workflow.

---

## Step 2 — Twilio Trigger Node

The first node used in the workflow is:

```text
Twilio Trigger
```

Purpose:

* Receives incoming WhatsApp messages
* Starts the workflow automatically
* Sends the user message to the AI Agent

---

## Step 3 — AI Agent Node

The next node is:

```text
AI Agent
```

Purpose:

* Understand the user's query
* Detect dates such as:

  * today
  * tomorrow
  * specific dates
* Decide when to use Google Calendar Tool
* Generate natural language replies

The AI Agent is connected to:

* OpenAI Chat Model
* Google Calendar Tool

---

## Step 4 — OpenAI Chat Model

The AI Agent uses:

```text
OpenAI Chat Model
```

OpenAI free credits were used for testing.

Purpose:

* Process natural language
* Understand meeting-related questions
* Generate human-like responses

---

## Step 5 — Google Calendar Tool

The Google Calendar Tool is connected as a tool to the AI Agent.

Configuration used:

```text
Resource: Event
Operation: Get Many
Calendar: Primary
```

Purpose:

* Fetch meetings/events from Google Calendar
* Count number of meetings
* Retrieve event titles and timings

---

## Step 6 — Send SMS/MMS/WhatsApp Message Node

The final node in the workflow is:

```text
Send an SMS/MMS/WhatsApp message
```

Purpose:

* Send the AI-generated response back to WhatsApp
* Display meeting count and timings to the user

---

# Example Outputs

## Example 1

### User Message

```text
How many meetings today?
```

### AI Response

```text
Today you have 3 meetings:

1. Team Standup — 10:00 AM
2. Client Discussion — 2:00 PM
3. Project Review — 6:30 PM
```

---

## Example 2

### User Message

```text
How many meetings tomorrow?
```

### AI Response

```text
Tomorrow you have 2 meetings:

1. UI Planning — 11:00 AM
2. Security Review — 4:00 PM
```

---

## Example 3

### User Message

```text
How many meetings on 9th May 2026?
```

### AI Response

```text
You have 1 meeting on 9th May 2026:

1. Final Demo Presentation — 3:00 PM
```

---

# Technologies Used

| Tool                | Purpose                        |
| ------------------- | ------------------------------ |
| n8n                 | Workflow automation            |
| Twilio              | WhatsApp messaging             |
| OpenAI              | AI understanding and responses |
| Google Calendar API | Fetching meetings/events       |

---

# Key Features

* WhatsApp-based interaction
* AI-powered meeting assistant
* Google Calendar integration
* Automatic meeting counting
* Natural language understanding
* Real-time automated replies

---

# Conclusion

This project demonstrates a complete AI-powered WhatsApp Calendar Assistant built using n8n automation.

The workflow successfully integrates:

* Twilio WhatsApp Sandbox
* OpenAI Chat Model
* Google Calendar Tool
* Automated WhatsApp replies

Users can naturally ask questions about their meetings and receive intelligent responses directly on WhatsApp.
