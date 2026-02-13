# Steam Gift — Step-by-step (real cURL)

## How to get an API key
All API requests require an `apikey` header.

To get your API key, contact DesslyHub manager:
- Telegram: https://t.me/DesslyHub_Manager
- Email: partner@desslyhub.com

## Base URL
https://desslyhub.com/api/v1/

## Flow
1) Get the games catalog to obtain `app_id`.
2) Get game details by `app_id` to obtain `package_id` and available regions.
3) Send the gift using customer's `invite_url`.
4) Receive `transaction_id` (status becomes `pending`).
5) Poll transaction status until `success` or `failed`.

## Real cURL examples

### 1) Get Games
```bash
curl --request GET \
  --url https://desslyhub.com/api/v1/service/steamgift/games \
  --header 'apikey: 1234567890'
```

### 2) Get Game by App ID
```bash
curl --request GET \
  --url https://desslyhub.com/api/v1/service/steamgift/games/12345 \
  --header 'apikey: 1234567890'
```

### 3) Gift
```bash
curl --request POST \
  --url https://desslyhub.com/api/v1/service/steamgift/sendgames \
  --header 'apikey: 1234567890' \
  --header 'content-type: application/json' \
  --data '
{
  "invite_url": "customer_url",
  "package_id": "12345",
  "region": "2_letter_country_code_(US, UK, DE etc.)"
}
'
```

### 4) Get Transaction Status
```bash
curl --request GET \
  --url https://desslyhub.com/api/v1/merchants/transaction/<transaction_id>/status \
  --header 'apikey: 1234567890'
```

## What to store on your side
- your internal `order_id`
- chosen `app_id` and `package_id`
- `region`
- customer `invite_url` (or your internal customer id)
- returned `transaction_id`
- final status (`success` / `failed`) + timestamps
