# DesslyHub API Examples (No-code)

This repo contains practical, copy-paste friendly integration examples for merchants using the DesslyHub API.

## Quick links (API Reference)
- Introduction: https://desslyhub.readme.io/reference/introduction
- Get Games: https://desslyhub.readme.io/reference/get_apiv1steamgames
- Get Game by App ID: https://desslyhub.readme.io/reference/get_apiv1steamgamesapp_id
- Gift: https://desslyhub.readme.io/reference/post_apiv1steamgift
- Get Transaction Status: https://desslyhub.readme.io/reference/get_apiv1statustransaction_id
- Error codes: https://desslyhub.readme.io/reference/error-codes

## Typical flow: Steam Gift
1. Authenticate every API request using an API key (provided by your DesslyHub manager).
2. Fetch the games catalog with appids via **Get Games**.
3. Get pricing/regions and the required `package_id` via **Get Game by App ID**.
4. Send a gift using buyer’s quick “add as friend” link via **Gift**.
5. DesslyHub returns a **transaction_id** and sets status to **pending**.
6. Poll **Get Transaction Status** until **success** or **failed**.

### Best practice
- Store a mapping between your internal `order_id` and the DesslyHub `transaction_id` for reconciliation and support.

## Contents
- /steam-gift — step-by-step Steam Gift scenario
- /transactions — status polling & reconciliation checklist
- /auth — how to use API key in tools (Postman/curl)
