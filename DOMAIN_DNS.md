# Domain and DNS

Create three `A` records pointing to the VPS public IP:
- `cli.your-domain.tld`
- `graf.your-domain.tld`
- `dashboard.your-domain.tld`

If using Cloudflare, set DNS only for initial ACME issuance, then proxy if desired. Keep HSTS in mind.
