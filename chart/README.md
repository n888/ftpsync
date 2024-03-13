# ftpsync

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

Helm chart for ftpsync to mirror a debian repository based on crontab sidecar and serving it via http

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| crontab.command[0] | string | `"crond"` |  |
| crontab.command[1] | string | `"-m"` |  |
| crontab.command[2] | string | `"-f"` |  |
| crontab.command[3] | string | `"-p"` |  |
| crontab.command[4] | string | `"-x"` |  |
| crontab.command[5] | string | `"sch"` |  |
| crontab.config | string | ```"MIRRORNAME=\"default.local\"\nTO=\"/var/www/debian\"\nLOGNAME=\"ftpsync\"\n\n# MAILTO=\"$LOGNAME\"\n# HUB=false\n\n########################################################################\n## Connection options\n########################################################################\n\nRSYNC_HOST=deb.debian.org\nRSYNC_PATH=\"debian\"\n# RSYNC_USER=\n# RSYNC_PASSWORD=\n\n########################################################################\n## Mirror information options\n########################################################################\n\n# INFO_MAINTAINER=\"Admins <admins@example.com>, Person <person@example.com>\"\n# INFO_SPONSOR=\"Example <https://example.com>\"\n# INFO_COUNTRY=DE\n# INFO_LOCATION=\"Example\"\n# INFO_THROUGHPUT=10Gb\n\n########################################################################\n## Include and exclude options\n########################################################################\n\nARCH_INCLUDE=\"all amd64 arm64 source\"\n# ARCH_EXCLUDE=\n\n########################################################################\n## Log option\n########################################################################\n\n# LOGDIR=\n"``` |  |
| crontab.entry | string | `"* */5 * * * ftpsync /opt/archvsync/bin/ftpsync-cron"` |  |
| crontab.image.pullPolicy | string | `"IfNotPresent"` |  |
| crontab.image.repository | string | `"ghcr.io/n888/ftpsync"` |  |
| crontab.image.tag | string | `"latest"` |  |
| crontab.livenessProbe.exec.command[0] | string | `"ls"` |  |
| crontab.livenessProbe.exec.command[1] | string | `"/"` |  |
| crontab.readinessProbe.exec.command[0] | string | `"ls"` |  |
| crontab.readinessProbe.exec.command[1] | string | `"/"` |  |
| crontab.resources | object | `{}` |  |
| crontab.volumeMounts[0].mountPath | string | `"/opt/archvsync/etc/ftpsync.conf"` |  |
| crontab.volumeMounts[0].name | string | `"ftpsync"` |  |
| crontab.volumeMounts[0].readOnly | bool | `true` |  |
| crontab.volumeMounts[0].subPath | string | `"ftpsync.conf"` |  |
| crontab.volumeMounts[1].mountPath | string | `"/var/spool/cron/crontabs/root"` |  |
| crontab.volumeMounts[1].name | string | `"crontab"` |  |
| crontab.volumeMounts[1].readOnly | bool | `true` |  |
| crontab.volumeMounts[1].subPath | string | `"crontabEntry"` |  |
| crontab.volumeMounts[2].mountPath | string | `"/var/www"` |  |
| crontab.volumeMounts[2].name | string | `"www"` |  |
| fullnameOverride | string | `""` |  |
| hostPath.enabled | bool | `false` |  |
| hostPath.path | string | `"/var/www"` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.additionalMounts | list | `[]` |  |
| persistence.additionalVolumes | list | `[]` |  |
| persistence.enabled | bool | `false` |  |
| persistence.existingClaim | string | `""` |  |
| persistence.size | string | `"1200Gi"` |  |
| persistence.storageClass | string | `""` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| securityContext | object | `{}` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |
| web.config | string | `"server {\n  listen 80 default_server;\n  listen [::]:80 default_server;\n\n  server_name _;\n\n  location / {\n    root /var/www;\n    autoindex on;\n  }\n}\n"` |  |
| web.image.pullPolicy | string | `"IfNotPresent"` |  |
| web.image.repository | string | `"ghcr.io/n888/ftpsync"` |  |
| web.image.tag | string | `"latest"` |  |
| web.ingress.annotations | object | `{}` |  |
| web.ingress.className | string | `""` |  |
| web.ingress.enabled | bool | `false` |  |
| web.ingress.hosts[0].host | string | `"default.local"` |  |
| web.ingress.hosts[0].paths[0].path | string | `"/"` |  |
| web.ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| web.ingress.tls[0].hosts[0] | string | `"default.local"` |  |
| web.ingress.tls[0].secretName | string | `"ftpsync-cert"` |  |
| web.livenessProbe.httpGet.path | string | `"/"` |  |
| web.livenessProbe.httpGet.port | string | `"http"` |  |
| web.readinessProbe.httpGet.path | string | `"/"` |  |
| web.readinessProbe.httpGet.port | string | `"http"` |  |
| web.resources | object | `{}` |  |
| web.service.port | int | `80` |  |
| web.service.type | string | `"ClusterIP"` |  |
| web.volumeMounts[0].mountPath | string | `"/etc/nginx/sites-available/default"` |  |
| web.volumeMounts[0].name | string | `"nginx"` |  |
| web.volumeMounts[0].readOnly | bool | `true` |  |
| web.volumeMounts[0].subPath | string | `"nginx.conf"` |  |
| web.volumeMounts[1].mountPath | string | `"/var/www"` |  |
| web.volumeMounts[1].name | string | `"www"` |  |
| web.volumeMounts[1].readOnly | bool | `true` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.13.1](https://github.com/norwoodj/helm-docs/releases/v1.13.1)
