# Authentication

All API requests require an API key passed via request header:

- Header name: `apikey`
- Example: `apikey: 1234567890`

## How to get an API key
Contact DesslyHub manager:
- Telegram: https://t.me/DesslyHub_Manager
- Email: partner@desslyhub.com

## Postman setup (recommended)
1. Create a Postman Environment (e.g., `DesslyHub`).
2. Add variable:
   - `API_KEY` = your key value
3. For each request, add a header:
   - Key: `apikey`
   - Value: `{{API_KEY}}`

## Security notes
- Never hardcode the API key in client-side code.
- Keep the key in server-side environment variables / secrets when possible.
