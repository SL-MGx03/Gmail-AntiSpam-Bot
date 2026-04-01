# Gmail Anti-Spam Bot

A Telegram bot that connects to your Gmail account, scans inbox messages, and helps identify potential spam/newsletters using AI.  
It also supports natural-language email search directly from Telegram.

## Features

- **Spam scanning**: Analyze inbox messages and generate a spam/security summary.
- **AI-powered email search**: Search Gmail messages with plain language queries.
- **Telegram interface**: Trigger scans and searches with simple bot commands.
- **Access control**: Restrict bot usage to configured sudo users.

## Tech Stack

- Python
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
- LangChain + LangGraph
- Google Gemini (`langchain-google-genai`)
- Gmail Toolkit (`langchain_google_community`)
- Gmail API (OAuth2)

## Project Structure

- `app.py` — Telegram bot entry point and command handlers
- `spam_engine.py` — AI workflows for spam scan and Gmail search
- `gmail_tools.py` — Gmail toolkit/credentials setup
- `sample.env` — Environment variable template
- `requirements.txt` — Python dependencies

## Requirements

- Python **3.10+** recommended
- A Telegram bot token (from [@BotFather](https://t.me/BotFather))
- Google Cloud OAuth credentials (`credentials.json`)
- Gmail API enabled in your Google Cloud project
- Gemini API key

## Setup

### 1) Clone the repository

```bash
git clone https://github.com/SL-MGx03/Gmail-AntiSpam-Bot.git
cd Gmail-AntiSpam-Bot
```

### 2) Create and activate a virtual environment

```bash
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

### 3) Install dependencies

```bash
pip install -r requirements.txt
```

### 4) Configure environment variables

Create a `.env` file based on `sample.env`:

```env
GOOGLE_API_KEY=your_google_ai_api_key
BOT_FATHER_TOKEN=your_telegram_bot_token
SUDO_USERS=123456789,987654321
```

> `SUDO_USERS` must be Telegram numeric user IDs separated by commas.

### 5) Add Google OAuth credentials

Place your OAuth client file as:

- `credentials.json`

On first run, OAuth flow will generate:

- `token.json`

## Running the Bot

```bash
python app.py
```

If startup is successful, you’ll see a log similar to:

- `Bot started. Sudo users: [...]`

## Telegram Commands

- `/start` — bot intro/status (sudo users only)
- `/scan` — scan inbox and generate spam/security report
- `/search <query>` — search Gmail using natural language  
  Example: `/search invoices from last month`

## Security Notes

- Never commit `.env`, `token.json`, or `credentials.json`.
- Restrict `SUDO_USERS` to trusted Telegram accounts only.
- Rotate compromised API keys/tokens immediately.

## Known Limitations

- Search/report output may be long and sent as a text file.
- Accuracy depends on model/tooling and mailbox data quality.
- Gmail API quotas and permissions can affect behavior.

## Troubleshooting

- **`credentials.json` not found**: Add Google OAuth client credentials file to project root.
- **Unauthorized Telegram access**: Verify your Telegram user ID is included in `SUDO_USERS`.
- **Gmail auth issues**: Delete `token.json` and re-authenticate.
- **Dependency errors**: Ensure virtual environment is active and requirements are installed.

## License

This project is licensed under the **GNU GPL v3**.  
See the [LICENSE](LICENSE) file for details.

---

## NOTE 

Please Use this Script only for education perpose only.
We are not responsible for any damaged caused physical or digital damage to any of your personal property.

---

If you find this project useful, consider starring the repository and contributing improvements.
