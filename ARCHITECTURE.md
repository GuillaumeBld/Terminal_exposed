# Architecture

```
[ Internet ]
     |
 [ Traefik, TLS, ACME ]
     | rules by Host header, middlewares for OAuth
     +--------------------------+-----------------------------+
     |                          |                             |
 [ control-dashboard ]   [ oauth2-proxy ]             [ grafana ]
     |                          ^                             ^
     | iframe to cli host       | forward auth                |
     |                          |                             |
 [ gcloud-ttyd ]  <----- internal network ----->  [ prometheus, cadvisor, node-exporter ]

Legend:
- public subdomains, dashboard, cli, graf
- infra network is internal, proxy network is Traefik public side
- gcloud-ttyd contains ttyd and Google Cloud CLI, runs as user cli
- no privileged mounts, no Docker socket exposure
```
