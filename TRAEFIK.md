# Traefik integration

Routers:
- `cli` routes Host rule `cli.domain`, service port `7681`
- `graf` routes Host rule `graf.domain`, service port `3000`
- `ctrl` routes Host rule `dashboard.domain`, service port `80`

Middlewares:
- `oauth@docker` from oauth2-proxy forward auth
- Optional `ipwhitelist`, `headers`, `compress`

Certificates:
- Use Traefik ACME with HTTP or TLS challenge.
