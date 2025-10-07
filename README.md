# Terminal Exposed, Control Dashboard

Purpose: expose a **web terminal** restricted to a container with Google Cloud CLI, fronted by Traefik and OAuth, and render **metrics** and a **control page**.

Scope: documentation only, meant to pair with your `docker-compose.yml` and related files.

## Key components
- Traefik, entrypoint and TLS termination, with middleware for auth and IP rules
- ttyd, web terminal bound to a non root shell inside a gcloud container
- oauth2-proxy, Google login, session cookies
- Prometheus, cAdvisor, node exporter, Grafana for metrics
- Static control page that embeds terminal and selected Grafana panels

## Quick start
1. Create a Docker network for Traefik if missing:
   ```bash
   docker network create proxy
   ```
2. Prepare `.env` values:
   ```bash
   GOOGLE_CLIENT_ID=...apps.googleusercontent.com
   GOOGLE_CLIENT_SECRET=...
   COOKIE_SECRET_32B=32_random_base64_bytes
   GRAFANA_ADMIN_PW=choose_a_strong_pw
   ```
3. Point DNS A records to your VPS:
   - `cli.your-domain.tld`
   - `graf.your-domain.tld`
   - `dashboard.your-domain.tld`
4. `docker compose up -d --build`
5. Visit `https://dashboard.your-domain.tld`, sign in with Google, run `gcloud init` in the terminal pane.

Security note: the terminal runs as a non root user, read only rootfs, no Docker socket, and is gated behind OAuth. Do not remove these controls.
