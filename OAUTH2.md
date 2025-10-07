# OAuth with oauth2-proxy

Provider: Google.

Console steps:
1. Go to Google Cloud Console, create OAuth 2.0 Client ID, Web application.
2. Authorized redirect URI: `https://dashboard.domain/oauth2/callback` and the same host for cli and graf if you split by app. With forward auth pattern, a single oauth2-proxy works, redirect URI is `https://dashboard.domain/oauth2/callback`.
3. Place client id and secret in `.env`.

Compose variables for oauth2-proxy are already set for forward auth.
