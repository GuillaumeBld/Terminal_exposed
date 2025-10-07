# Backup and disaster recovery

Minimal plan:
- Daily snapshot of `gcloud_home` named volume
- Export Grafana dashboards as JSON and keep in git
- Keep a copy of `.env` in a password manager notes field

Recovery:
1. Restore DNS to the new IP.
2. Recreate `proxy` network and launch compose.
3. Restore `gcloud_home` from backup tar to the named volume.
