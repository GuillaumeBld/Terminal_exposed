# Metrics stack

Exporters:
- node-exporter on host network, exposes 9100
- cAdvisor in container, exposes 8080

Prometheus config:
- See `prometheus.yml` with two scrape jobs.

Grafana:
- Add Prometheus datasource URL `http://prometheus:9090`
- Import common dashboards for Linux host and Docker overview.
- Copy a panel share link, paste in `site/index.html` iframe `src` value.
