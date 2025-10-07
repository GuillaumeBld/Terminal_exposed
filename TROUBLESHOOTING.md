# Troubleshooting

Sign in loop:
- Check cookie domain and correct callback URL in Google console.
- Verify oauth2-proxy time is correct, use the VPS NTP service.

404 from Traefik:
- Host rule mismatch, check labels and DNS.

Terminal blank screen:
- Confirm `ttyd` is listening on 7681 in container.
- Confirm iframe `src` points to the correct domain.

Grafana cannot find datasource:
- Set Prometheus URL `http://prometheus:9090` and save.
