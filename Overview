Sentiment Feedback Intelligence Agent - MVP Documentation

🧠 Overview

The Sentiment Feedback Intelligence Agent is a Power Automate-based solution enhanced with Azure OpenAI to analyze customer sentiment from recent email conversations. This Minimum Viable Product (MVP) was built for a hackathon and integrates:

Microsoft Graph API (via HTTP)

Dynamic content filtering and HTML parsing

Azure OpenAI sentiment analysis

Power Virtual Agent integration for conversational return

✅ MVP Goals

Automatically pull recent emails from a defined sender.

Extract and clean the body content of the emails.

Analyze emotional tone using Azure OpenAI.

Return a summarized sentiment score or insight to the virtual agent.

🧱 Stack & Services Used

Component

Description

Power Automate

Core flow orchestration engine

Microsoft Graph API

Pulls emails from user's mailbox

Azure OpenAI (GPT 3.5)

Performs language-based sentiment analysis

HTML to Text Connector

Extracts readable content from HTML emails

Power Virtual Agent

Entry/exit interface to query and display sentiment

🔁 Flow Structure

1. Trigger

Starts via Power Virtual Agent

Accepts two dynamic inputs: clientName, timePeriod

2. HTTP - Microsoft Graph API

Authenticates via client_credentials

Endpoint:

https://graph.microsoft.com/v1.0/me/messages?$top=100&$search="from:{clientName}"

Returns latest emails from the specified sender

3. Filter Array

Filters only emails within a valid timePeriod

Optional enhancement: ISO date filter using receivedDateTime

4. Select & Compose

Selects body.body.content from each email

Joins multiple email bodies into one string

5. Html to Text (inside a loop)

Converts each HTML body to plain text using Power Automate connector

6. Final Compose

Concatenates all cleaned plain-text bodies

7. Azure OpenAI - HTTP (POST)

Sends text to Azure OpenAI for analysis

Example payload:

{
  "messages": [
    {
      "role": "system",
      "content": "You are a sentiment analysis expert. Summarize sentiment of the following customer email(s)."
    },
    {
      "role": "user",
      "content": "<email content goes here>"
    }
  ],
  "temperature": 0.3,
  "max_tokens": 200,
  "model": "gpt-35-turbo"
}

8. Parse JSON

Parses the OpenAI response to extract choices[0].message.content

9. Respond to the Agent

Returns sentiment text back to the user through the chatbot

⚙️ Authentication Details

Microsoft Graph Token:

Client credentials flow

Required Headers:

{
  "Content-Type": "application/x-www-form-urlencoded"
}

Required Body:

grant_type=client_credentials
&client_id=<client-id>
&client_secret=<secret>
&scope=https%3A%2F%2Fgraph.microsoft.com%2F.default

Azure OpenAI Setup:

Deployed GPT-3.5 model on Azure OpenAI Studio

Generated deployment name and API key

📦 Sample Output

{
  "sentimentassessment": "The customer sentiment is positive. The user expresses gratitude and is satisfied with the recent delivery."
}

🚀 Future Enhancements

Add time-based filtering (last X days)

Visual charts for multi-email trends

Integrate with CRM (e.g. Dynamics, Salesforce)

Train model for domain-specific tone nuances

📁 Folder Structure (GitHub)

📁 sentiment-agent-mvp
├── README.md
├── documentation.md <-- (this file)
├── assets/
│   └── screenshots.png
├── flow-export.zip
└── .env.example

👥 Contributors

[Your Name Here]

AI/Automation Engineer

Hackathon Submission, April 2025

📄 License

MIT

