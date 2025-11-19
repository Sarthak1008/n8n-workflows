# 📦 n8n-workflows  
Automation workflows built using **n8n**, including LinkedIn job search automation and Facebook Messenger AI auto-reply bot.

---

![Workflow Diagram](https://raw.githubusercontent.com/Sarthak1008/n8n-workflows/main/n8n%20Triggers.png)


## 1️⃣ LinkedIn Job Search Automation  
Automatically fetches job listings from LinkedIn every day and emails you a formatted HTML report.

### ✨ Features
- Fetches jobs using **RapidAPI – LinkedIn Jobs Search API**  
- Filters by:
  - Job title (e.g., "Java Developer")
  - Location: India
  - Posted: Past 24 hours
- Cleans and processes external job URLs  
- Generates a clean HTML email table  
- Sends the report to Gmail  
- Runs daily at **8:30 PM**

### 🧩 Workflow Nodes
- Schedule Trigger  
- Edit Fields (Set)  
- HTTP Request (LinkedIn API)  
- Code Node (process job data)  
- Code Node (build email template)  
- Email Send (SMTP)

### 📁 File
`Job Search LinkedIn.json`

### 📊 Simplified Flow
Schedule Trigger → Edit Fields → LinkedIn API → Format Job Data → Build Email HTML → Send Email
---

## 2️⃣ Facebook Auto-Reply Bot (Messenger Webhook + AI)

Webhook-based workflow that listens to Facebook Messenger, verifies the webhook, and replies with an AI-generated message.

### ✨ Features
- Facebook Webhook verification using `hub.challenge`
- Receives messages from Facebook Messenger
- AI-generated replies using OpenAI (chatgpt-4o-latest)
- Maintains chat context with Memory Buffer Window
- Sends reply to user via Facebook Graph API
- Has fallback response for empty messages

### 🧩 Workflow Nodes
- Webhook (GET + POST)  
- IF (Webhook verification)  
- Respond to Webhook  
- AI Agent  
- OpenAI Chat Model  
- Memory Buffer Window  
- HTTP Request (Facebook Send Message API)

### 📁 File
`FaceBook trigger reply.json`

### 📊 Simplified Flow

Webhook → IF (Token Check)
├── Respond With hub.challenge
└── AI Agent → Facebook Send Message API


---

## 📥 Importing Workflows Into n8n

1. Open **n8n**
2. Go to **Workflows → Import from File**
3. Upload:
   - `Job Search LinkedIn.json`
   - `FaceBook trigger reply.json`
4. Configure your credentials:
   - RapidAPI Key  
   - Facebook Page Access Token  
   - OpenAI API Key  
   - SMTP credentials (Gmail)
5. Activate workflows

---

## 📚 Requirements

| Component | Requirement |
|----------|-------------|
| n8n Version | v1.5+ |
| API Keys | RapidAPI, Facebook Graph API, OpenAI |
| SMTP | Gmail / Any SMTP |
| Server for webhook stability | Recommended |

---

## 🤝 Contributing  
Feel free to raise issues or submit PRs to improve these workflows.

---

## 📄 License  
MIT License

---
