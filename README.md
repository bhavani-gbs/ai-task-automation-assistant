# 🤖 AI Task Automation Assistant

> Convert any task into structured output and store it in Notion — automatically.

![Pipeline](https://img.shields.io/badge/Pipeline-Webhook→AI→Notion-7c6aff?style=flat-square)
![n8n](https://img.shields.io/badge/Automation-n8n-ff6d5a?style=flat-square)
![Gemini](https://img.shields.io/badge/AI-Gemini%202.5%20Flash-4285F4?style=flat-square)
![Notion](https://img.shields.io/badge/Storage-Notion-000000?style=flat-square)
![Free](https://img.shields.io/badge/Cost-100%25%20Free-4ade80?style=flat-square)

---

## 📌 What Is This?

A fully automated AI pipeline where you type a task, and the system:

1. Sends it to **Gemini AI** for processing
2. Extracts **summary, action steps, priority & time estimate**
3. Automatically saves everything to a **Notion database**
4. Displays the result in a clean **web UI**

No manual formatting. No copy-pasting. Just type and done.

---

## 🎯 Pipeline Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Web UI     │────▶│  n8n        │────▶│  Gemini AI  │────▶│   Notion    │
│  (HTML/JS)  │     │  Webhook    │     │  API        │     │  Database   │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
   User Input         Automation          AI Processing        Auto Storage
```

---

## ✨ Features

- 🧠 **AI Processing** — Gemini 2.5 Flash converts raw tasks into structured data
- 📋 **Auto Storage** — Every task saved to Notion with all fields filled
- 🎨 **Clean UI** — Web interface with example chips & live results
- ⚡ **Fast** — End-to-end in under 5 seconds
- 🆓 **100% Free** — Uses free tiers of all APIs
- 🔒 **Secure** — API keys never exposed in frontend

---

## 🛠️ Tech Stack

| Tool | Purpose | Cost |
|------|---------|------|
| [n8n](https://n8n.io) | Workflow automation (self-hosted) | Free |
| [Google Gemini API](https://aistudio.google.com) | AI task processing | Free |
| [Notion API](https://notion.so/my-integrations) | Structured data storage | Free |
| HTML/CSS/JS | Frontend web UI | Free |

---

## 📸 Output Example

**Input:**
```
Build a portfolio website in 7 days
```

**Auto-saved to Notion:**

| Field | Value |
|-------|-------|
| Task Name | Build Portfolio Website |
| Summary | The goal is to create a functional and visually appealing portfolio... |
| Action Steps | Step 1: Define content & design (Day 1) \| Step 2: Gather content (Day 2-3) \| ... |
| Priority | 🔴 High |
| Time Estimate | 7 days |
| Created At | 2026-04-04 |

---

## ⚙️ Setup Instructions

### Prerequisites
- [Node.js](https://nodejs.org) (LTS version)
- Google account (for Gemini API)
- Notion account

---

### Step 1 — Install & Start n8n
```bash
npm install -g n8n
n8n start
```
Open browser → `http://localhost:5678`

---

### Step 2 — Get Your API Keys

**Gemini API Key (Free):**
1. Go to [https://aistudio.google.com](https://aistudio.google.com)
2. Click "Get API Key" → "Create API Key"
3. Copy and save it

**Notion Integration Token:**
1. Go to [https://notion.so/my-integrations](https://notion.so/my-integrations)
2. Click "+ New Integration" → name it "AI Task Assistant"
3. Copy the token

**Notion Database ID:**
1. Create a Notion database with these columns:
   - Task Name (Title)
   - Summary (Text)
   - Action Steps (Text)
   - Priority (Select: High/Medium/Low)
   - Time Estimate (Text)
   - Created At (Date)
2. Open the database as full page
3. Copy the ID from the URL (32-character string before `?v=`)

---

### Step 3 — Import Workflow to n8n
1. Open n8n → click **"Import from file"**
2. Select `workflow.json`
3. Update these placeholders with your real keys:
   - `YOUR_GEMINI_API_KEY` → in HTTP Request node URL
   - `YOUR_NOTION_API_TOKEN` → in Send to Notion node headers
   - `YOUR_NOTION_DATABASE_ID` → in Send to Notion node body
4. Click **"Active"** toggle to enable

---

### Step 4 — Connect Notion Integration
1. Open your Notion database
2. Click "..." → "Connections"
3. Search and connect "AI Task Assistant"

---

### Step 5 — Open the UI
1. Open `index.html` in your browser
2. Make sure n8n is running
3. Type any task and click **"Process & Save to Notion →"**

---

## 📁 Project Structure

```
ai-task-automation-assistant/
│
├── index.html          # Web UI — type tasks here
├── workflow.json       # n8n automation workflow (import this)
├── .env.example        # API key placeholders
├── .gitignore          # Ignores sensitive files
└── README.md           # This file
```

---

## 🔑 Environment Variables

Create a `.env.example` file (never commit real keys):

```bash
GEMINI_API_KEY=your_gemini_api_key_here
NOTION_API_TOKEN=your_notion_token_here
NOTION_DATABASE_ID=your_notion_database_id_here
```

---

## 🚀 How It Works (Technical)

1. **Webhook Node** — n8n listens for POST requests at `/webhook/task-input`
2. **HTTP Request Node** — Sends task to Gemini API with a structured prompt
3. **Code Node** — Parses Gemini's JSON response into clean fields
4. **HTTP Request Node** — Posts structured data to Notion via Pages API

---

## 📄 License

MIT License — free to use and modify.

---


## 👨‍💻 Author

**G Bhavani Shanth**
B.Tech AIML | Woxsen University

[![GitHub](https://img.shields.io/badge/GitHub-bhavani-gbs-181717?style=flat-square&logo=github)](https://github.com/bhavani-gbs)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-bhavani-shanth-gottipalli-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/bhavani-shanth-gottipalli/)

> ⭐ Star this repo if you found it useful!
