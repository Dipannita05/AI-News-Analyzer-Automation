# 📰 AI-Powered Automated News Analyzer

An AI-powered news analysis automation workflow built with **n8n, NewsAPI, Google Gemini, HTML, and Gmail**.

The workflow accepts a topic from a user, retrieves relevant news articles through NewsAPI, passes the retrieved information to a Google Gemini-powered AI Agent for structured analysis, generates the result as HTML, and automatically delivers the formatted report by email.

## 🚀 Project Overview

Researching a topic manually can require searching multiple news sources, reading articles, identifying important developments, organizing the information, and formatting the final report.

This project automates that pipeline:

**User Topic → n8n Form → NewsAPI → Gemini AI Agent → HTML Report → Gmail**

## 🔄 Workflow

1. **User Input** — An n8n form collects the topic to research and the recipient email address.
2. **News Retrieval** — An HTTP Request node calls the NewsAPI `everything` endpoint using the submitted topic. The current workflow requests English results, sorts them by publication date, and requests up to 5 articles.
3. **AI Analysis** — A Google Gemini-powered AI Agent receives the retrieved news information and is instructed to produce a factual, neutral, structured news analysis.
4. **HTML Generation** — The Agent is instructed to return only valid, semantic HTML so the report can be rendered directly in an email.
5. **Email Delivery** — The generated HTML is passed to Gmail and sent to the email address supplied in the form.

## 🧠 Analysis Structure

The AI instructions are designed to produce sections such as:

- Headline
- Executive Summary
- What Happened
- Key Facts & Developments
- Timeline
- Key People / Organizations Involved
- Why It Matters
- Impact / Implications
- Different Perspectives or Reactions
- What Happens Next
- Uncertainties / Controversies, when applicable
- Sources

The prompt also instructs the model to distinguish verified facts, official statements, opinions, analysis, and unconfirmed information, and to avoid fabricating facts, statistics, quotations, sources, or URLs.

## 🏗️ Architecture

```text
┌──────────────────────┐
│      User Form       │
│   Topic + Email      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    HTTP Request      │
│       NewsAPI        │
│  Retrieve Articles   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│      AI Agent        │
│    Google Gemini     │
│  Analyze & Structure │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│     HTML Report      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│        Gmail         │
│  Automated Delivery  │
└──────────────────────┘
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **n8n** | Workflow automation and orchestration |
| **NewsAPI** | News article retrieval |
| **Google Gemini** | AI-powered analysis and report generation |
| **HTTP / REST API** | Communication with NewsAPI |
| **HTML** | Structured report formatting |
| **Gmail** | Automated report delivery |

## ✨ Key Features

- Topic-based news retrieval
- Automated API integration
- AI-powered news analysis
- Structured multi-section reports
- Timeline and key-developments extraction
- Source listing and attribution instructions
- HTML-formatted email output
- Automated email delivery
- Dynamic user input and email routing

## 📸 Demo

### n8n Workflow

![n8n workflow](screenshots/workflow.png)

### Generated News Report — Overview

![Generated news report](screenshots/generated-report-1.png)

### Generated News Report — Timeline & Analysis

![Timeline and analysis](screenshots/generated-report-2.png)

## 📁 Repository Structure

```text
AI-News-Analyzer-Automation/
├── README.md
├── workflow/
│   └── AI-News-Analyzer-Workflow.json
└── screenshots/
    ├── workflow.png
    ├── generated-report-1.png
    └── generated-report-2.png
```

## 🔐 Setup & Security

The workflow JSON in this repository is a **sanitized template**.

Before using it:

1. Import the JSON into n8n.
2. Add your own **NewsAPI key** in the HTTP Request node.
3. Configure your own **Google Gemini credential**.
4. Configure your own **Gmail credential**.
5. Test the workflow with a topic and recipient email.

**No private API keys or OAuth credentials are included in this repository.**

## 📚 What I Learned

- Building automated workflows with n8n
- Integrating external REST APIs
- Passing dynamic form data between workflow nodes
- Working with JSON-based API responses
- Configuring AI Agents and LLM prompts
- Prompt engineering for structured outputs
- Generating semantic HTML with an LLM
- Automating email delivery
- Testing and debugging multi-step workflows

## 🔮 Future Improvements

- Integrate multiple news providers
- Add duplicate article detection
- Add source credibility scoring
- Add sentiment analysis
- Add scheduled daily/weekly reports
- Track topics over time
- Add a dashboard for historical news analysis

## 👩‍💻 Author

**Dipannita Pramanik**  
B.Sc. Data Science

---

*This project demonstrates the integration of APIs, AI/LLMs, workflow automation, structured output generation, and automated communication in an end-to-end application.*
