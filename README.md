# Autonomous Executive Inbox & Telegram Action Hub (n8n + AI)

An enterprise-ready **Human-in-the-Loop (HITL)** automation system built with **n8n**, **Vercel AI Gateway**, **Telegram Bot API**, and **Gmail**.

---

## 📁 Repository Structure

```
├── docker-compose.yml              # n8n container service with persistent SQLite volume
├── .env.example                    # Environment variable template
├── .env                            # Active environment configuration
├── workflows/
│   ├── executive_inbox_triage.json # Ingestion, sanitization, AI evaluation & Telegram alert
│   └── telegram_action_handler.json# Telegram callback queries, dispatching & Gmail replies
└── docs/
    └── PORTFOLIO_CASE_STUDY.md     # lencho.dev showcase copy, video script, & Upwork proposal template
```

---

## 🚀 Quick Start

### 1. Launch the n8n Container
```bash
docker compose up -d
```
The n8n editor will be accessible at: **[http://localhost:5678](http://localhost:5678)**

### 2. Configure Environment Variables
Edit your `.env` file with your credentials:
```bash
# Vercel AI Gateway
VERCEL_AI_GATEWAY_URL=https://api.gateway.vercel.com/v1
VERCEL_AI_GATEWAY_API_KEY=your_key_here
DEFAULT_AI_MODEL=anthropic/claude-3-5-sonnet

# Telegram
TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_CHAT_ID=your_chat_id
```

### 3. Import Workflows into n8n
1. Open **[http://localhost:5678](http://localhost:5678)**.
2. In the left navigation, click **Workflows** $\rightarrow$ **Add Workflow** $\rightarrow$ **Import from File**.
3. Select `workflows/executive_inbox_triage.json` and `workflows/telegram_action_handler.json`.
4. Click **Test step** or activate the workflows.

---

## 🛡️ Key Features
- **Token Efficient:** Strips raw HTML and truncates oversized payloads before passing to the LLM.
- **Multi-Model Support:** Uses Vercel AI Gateway to seamlessly switch between Claude, GPT-4o, or open-source models without node rewiring.
- **Idempotent Telegram Controls:** Prevents accidental double-sends by editing button state upon receipt.
- **Showcase Ready:** Complete portfolio write-up and video script in `docs/PORTFOLIO_CASE_STUDY.md`.
