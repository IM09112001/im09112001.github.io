# Ruslan Event Site — Barbucks Payment API

FastAPI backend that creates Telegram payment invoice links for the Barbucks coffee shop Web App. Integrates with Telegram's payment API to generate invoice URLs returned to the Telegram mini-app frontend.

## Tech Stack

- Python 3.10+
- [FastAPI](https://fastapi.tiangolo.com/)
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
- Uvicorn (ASGI server)
- python-dotenv

## Prerequisites

- Python 3.10+
- Telegram Bot token from [@BotFather](https://t.me/BotFather)
- Telegram payment provider token (from BotFather → Payments)

## Setup

```bash
git clone https://github.com/IM09112001/ruslan-event-site.git
cd ruslan-event-site

python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
# Edit .env with your tokens
```

## Environment Variables

```
TELEGRAM_TOKEN=   # Your bot token from @BotFather
INVOICE_TOKEN=    # Payment provider token from @BotFather → Payments
```

## Running

```bash
uvicorn server:app --reload --host 0.0.0.0 --port 8000
```

## API

### `GET /api/invoice`

Creates a Telegram payment invoice link.

**Request body:**
```json
{
  "order_data": [{"id": 1, "quantity": 2}],
  "comment": "Extra hot",
  "user_id": 123456789,
  "user_hash": "unique-payload-hash"
}
```

**Response:**
```json
{"url": "https://t.me/invoice/..."}
```

## Menu Items

16 Barbucks coffee drinks with prices in UZS (Uzbek Som).

## License

MIT
