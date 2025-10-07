# Control dashboard page

The Nginx container serves `site/index.html` which renders two iframes:
- Left, the terminal at `https://cli.domain`
- Right, a Grafana panel at `https://graf.domain` with dark theme

Change the layout by editing CSS in the head section. Keep iframes restricted to same origin policies, avoid embedding any untrusted sites.
