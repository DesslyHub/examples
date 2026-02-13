# Transactions — Status checks & reconciliation

## How to get an API key
All API requests require an `apikey` header.

To get your API key, contact DesslyHub manager:
- Telegram: https://t.me/DesslyHub_Manager
- Email: partner@desslyhub.com

## Base URL
https://desslyhub.com/api/v1/

## Endpoint: Get Transaction Status
https://desslyhub.com/api/v1/merchants/transaction/{transaction_id}/status

### cURL example
```bash
curl --request GET \
  --url https://desslyhub.com/api/v1/merchants/transaction/<transaction_id>/status \
  --header 'apikey: <YOUR_API_KEY>'
```

## Status model (high level)
- `pending` — processing
- `success` — completed
- `failed` — not completed

## Recommended polling checklist
- After calling `Gift`, store the returned `transaction_id` immediately.
- Start polling transaction status:
  - first check after a short delay (a few seconds),
  - then every 5–15 seconds (increase interval if you have many orders).
- Stop active polling after a reasonable time window and switch to background checks if needed.
- When status becomes final:
  - `success` → finalize customer flow and store completion time,
  - `failed` → show a clear message to the buyer and follow your retry/support policy.

## Support checklist (when contacting DesslyHub)
Provide:
- your internal `order_id`
- `transaction_id`
- timestamp(s)
- endpoint used: `Gift`
- last known status (and response if possible)

## Security notes
- Never expose the API key in client-side code.
- Rotate the API key if you suspect it was leaked.
