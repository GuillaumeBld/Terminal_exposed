# Deployment

Prereqs:
- Debian 13 on VPS, Docker and Docker Compose plugin installed
- Traefik already running on external network `proxy` with `websecure` entrypoint

Steps:
1. Clone the repository or copy the compose bundle.
2. Create `.env` with required variables, see CONFIGURATION.md.
3. Set DNS for the three subdomains.
4. `docker compose up -d --build`.
5. First login will create OAuth session, Grafana admin password is read from env.

Verify:
- `docker ps` shows gcloud-ttyd, oauth2-proxy, grafana, prometheus, cadvisor
- `curl -I https://cli.domain` returns 200 after auth
- Grafana datasource points to `http://prometheus:9090`
