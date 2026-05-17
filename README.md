# 🤖 AI-Powered Sales CRM Pipeline

> An intelligent, fully automated sales pipeline that qualifies leads using AI, sends personalized emails, and logs everything to Google Sheets — built with n8n, Groq LLM, and Brevo.

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-orange?style=flat&logo=n8n)
![AI](https://img.shields.io/badge/AI-Groq%20LLaMA%203-blue?style=flat)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Logging-green?style=flat&logo=google-sheets)
![Brevo](https://img.shields.io/badge/Email-Brevo-purple?style=flat)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

---

## 📌 Problem Statement

Sales teams waste hours manually reviewing leads, sending follow-up emails, and updating CRM sheets. This pipeline automates the entire process — from lead intake to qualification to outreach — using AI to make smarter decisions instantly.

---

## ✨ Features

- 🧠 **AI Lead Qualification** — LLaMA 3 scores every lead 1-10 and decides if they're worth pursuing
- 📧 **Automated Personalized Emails** — qualified leads get a warm welcome, unqualified ones get a polite rejection
- 📊 **Auto Google Sheets Logging** — every lead is logged with score, priority, and reason
- ⚡ **Real-time Processing** — entire pipeline runs in under 10 seconds
- 🔀 **Smart Routing** — IF/ELSE logic routes leads to the right email branch automatically

---

## 🧠 How It Works

```
Lead submits contact form
          ↓
    Webhook receives data
          ↓
  Groq LLaMA 3 qualifies lead
  (returns score, priority, reason)
          ↓
     Code node parses AI response
          ↓
        IF score > 5
       ↙           ↘
  ✅ Qualified    ❌ Unqualified
  Welcome Email   Rejection Email
       ↓                ↓
  Log to Google Sheets (both branches)
```

1. A lead fills out a contact form (or a webhook is triggered)
2. The lead's name, company, budget, and message are sent to **Groq's LLaMA 3** model
3. AI returns a **JSON response** with score (1-10), qualified (true/false), priority (high/medium/low), and reason
4. A **Code node** parses and cleans the AI response
5. An **IF node** routes the lead based on score
6. **Brevo** sends the appropriate email automatically
7. All data is logged to **Google Sheets** for tracking

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| `n8n` | Workflow automation and orchestration |
| `Groq API (LLaMA 3.3-70b)` | AI lead qualification and scoring |
| `Brevo API` | Automated email sending |
| `Google Sheets API` | Lead data logging and CRM |
| `Webhook` | Lead intake trigger |

---

## 📂 Project Structure

```
ai-sales-crm-pipeline/
├── AI Sales CRM Pipeline.json   # n8n workflow (import this directly)
└── README.md
```

---

## ▶️ Getting Started

### Prerequisites
- [n8n](https://n8n.io) installed locally or on cloud
- [Groq API key](https://console.groq.com) (free)
- [Brevo API key](https://brevo.com) (free)
- Google account with Sheets API enabled

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/niharikaaa2/ai-sales-crm-pipeline.git

# 2. Open n8n
n8n

# 3. Import the workflow
# In n8n → click "..." → Import → select "AI Sales CRM Pipeline.json"
```

### Configuration

Replace these placeholders in the workflow:

| Placeholder | Replace With |
|------------|-------------|
| `YOUR_GROQ_API_KEY` | Your Groq API key |
| `YOUR_BREVO_API_KEY` | Your Brevo API key |
| `YOUR_NAME` | Your name |
| `YOUR_EMAIL` | Your verified sender email |

### Testing

Send a test lead via curl:

```bash
curl -X POST "YOUR_WEBHOOK_URL" \
-H "Content-Type: application/json" \
-d '{
  "name": "Rahul Sharma",
  "company": "Tech Startup Mumbai",
  "budget": "50000",
  "email": "rahul@example.com",
  "message": "We need CRM automation for our 20 person sales team urgently"
}'
```

---

## 📈 Example Output

**AI Qualification Response:**
```json
{
  "score": 8,
  "qualified": true,
  "priority": "high",
  "reason": "Lead has a defined need and budget, indicating clear purchase intent."
}
```

**Google Sheets Log:**

| Name | Company | Budget | Score | Priority | Qualified |
|------|---------|--------|-------|----------|-----------|
| Rahul Sharma | Tech Startup Mumbai | 50000 | 8 | high | true |

---

## 🔮 Future Improvements

- [ ] **Follow-up automation** — auto email if no reply in 2 days
- [ ] **Slack notifications** — alert sales team for high priority leads
- [ ] **Web form integration** — connect to Typeform or Google Forms
- [ ] **Dashboard** — real-time lead analytics in Google Sheets
- [ ] **CRM integration** — sync with HubSpot or Notion

---

## 📄 License

This project is licensed under the MIT License.

---

## 👩‍💻 Author

**Niharika** — [@niharikaaa2](https://github.com/niharikaaa2)

*Built as part of my AI & Automation portfolio. Open to internship opportunities in AI/ML/Automation!*
