# Security hardening

Controls used:
- OAuth login using oauth2-proxy in front of every public router
- TLS via Traefik, certificates from ACME, HSTS can be enabled
- Non root shell, user `cli`, container runs with `no-new-privileges`
- Read only root filesystem for the terminal container, tmpfs for cache
- No Docker socket in any service, no host mounts except exporters
- Optional IP allowlist at Traefik, example:
  ```yaml
  traefik.http.middlewares.officeonly.ipwhitelist.sourcerange=203.0.113.0/24,198.51.100.7/32
  traefik.http.routers.cli.middlewares=oauth@docker,officeonly@docker
  ```

Secrets:
- `COOKIE_SECRET_32B` must be 32 random bytes base64, rotate on compromise
- `GRAFANA_ADMIN_PW` must be strong, rotate in line with your policy
- OAuth client id and secret are stored in `.env`. Avoid committing `.env` to git.

Session scope:
- Set short session lifetimes in oauth2-proxy if risk appetite is low:
  ```env
  OAUTH2_PROXY_COOKIE_REFRESH=15m
  OAUTH2_PROXY_COOKIE_EXPIRE=2h
  ```

Abuse surface:
- Disable write access to terminal container root. Only `$HOME` is persisted in a named volume for `gcloud` tokens.
- Treat any shell as high risk. Keep a narrow egress firewall if possible.
