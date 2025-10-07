# Operations, SRE notes

Backups:
- Volume `gcloud_home` contains gcloud tokens and config. Back it up.
- Prometheus data is ephemeral in this minimal setup. If you need retention, mount a volume.

Updates:
- Redeploy containers with `docker compose pull && docker compose up -d`

Monitoring:
- Add alert rules in Prometheus if you extend the stack.

Logs:
- `docker logs -f gcloud-ttyd`
- `docker logs -f oauth2-proxy`
- `docker logs -f grafana`
