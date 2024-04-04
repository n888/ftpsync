# Debian `ftpsync` helm chart
A Kubernetes Helm Chart for running Debian's mirror script behind an Nginx webserver, triggered by a crontab sidecar container.

# Installing the chart
```bash
helm repo add ftpsync https://n888.github.io/ftpsync/
helm install ftpsync ftpsync/ftpsync
```

# Links
* Setting up a Debian archive mirror: https://www.debian.org/mirror/ftpmirror
* `ftpsync` source: https://salsa.debian.org/mirror-team/archvsync
