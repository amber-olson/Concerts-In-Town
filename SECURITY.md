# Security Policy

## Setup Instructions

### ⚠️ Important: Protect Your API Keys

1. **Get Your Ticketmaster API Key**
   - Visit https://developer.ticketmaster.com/
   - Register for a free account
   - Create a new API key

2. **Create Your `.env` File**
   ```bash
   cp .env.example .env
   ```

3. **Add Your API Key**
   - Open `.env` in your editor
   - Replace `your_api_key_here` with your actual key
   - **Never commit this file** (.gitignore protects it)

4. **Keep Your `.env` Secret**
   - Never share or commit `.env`
   - Never paste it in issues, pull requests, or chats
   - Keep it only on your local machine

## API Key Security Best Practices

- ✅ Use `.env` files for local development
- ✅ Rotate API keys regularly
- ✅ Monitor API usage for suspicious activity
- ✅ Use environment variables in production
- ✅ Keep dependencies updated
- ❌ Never hardcode secrets in code
- ❌ Never commit `.env` files
- ❌ Never share API keys publicly

## If Your API Key is Compromised

1. **Immediately revoke it** at https://developer.ticketmaster.com/
2. **Generate a new key**
3. **Update your `.env` file**

## Reporting Security Issues

If you discover a security vulnerability in this repository, please email security@example.com instead of using the issue tracker.
