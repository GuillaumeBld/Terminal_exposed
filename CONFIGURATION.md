# Configuration

### Environment variables
```
GOOGLE_CLIENT_ID=xxx.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=xxx
COOKIE_SECRET_32B=base64_random_32B
GRAFANA_ADMIN_PW=StrongPassword
```

### Domains and TLS
- Replace `cli.example.com`, `graf.example.com`, `dashboard.example.com` with your domains in labels.
- Traefik must have `websecure` entrypoint and ACME enabled.

### Traefik network
- Compose expects an external Docker network named `proxy`:
  ```bash
  docker network create proxy
  ```
