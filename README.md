# DesslyHub API Examples (No-code)

This repository contains practical, copy-paste friendly integration examples for merchants using the DesslyHub API.

## Getting an API key
All API requests require an `apikey` header.

To get your API key, contact DesslyHub manager:
- Telegram: https://t.me/DesslyHub_Manager
- Email: partner@desslyhub.com

## Base URL
https://desslyhub.com/api/v1/

## Typical flow: Steam Gift (high level)
1) Fetch games catalog (Get Games) to obtain `app_id`.
2) Fetch game details (Get Game by App ID) to obtain `package_id`, pricing/regions.
3) Send gift (Gift) using customer `invite_url`.
4) Receive `transaction_id` (status becomes `pending`).
5) Check final status (Get Transaction Status) until `success` or `failed`.

### Best practice
- Store a mapping between your internal `order_id` and the DesslyHub `transaction_id` for reconciliation and support.

## Contents
- /auth — API key usage + Postman tips
- /steam-gift — step-by-step Steam Gift scenario + real cURL examples
- /transactions — status polling & reconciliation checklist
