# LimeSurvey

![Version: 0.2.63](https://img.shields.io/badge/Version-0.2.63-informational?style=for-the-badge)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=for-the-badge)
![AppVersion: 6.5.11](https://img.shields.io/badge/AppVersion-6.5.11-informational?style=for-the-badge)

## Description

Limesurvey is the number one open-source survey software. This chart uses the excellent container image from Adam Zammit of the Australian Consortium for Social and Political Research Incorporated (ACSPRI).

## Usage

```console
helm repo add area-42 https://area-42.github.io/helm-charts
helm repo update

helm install limesurvey \
  --set mariadb.auth.rootPassword=changeOnInstall \
  area-42/limesurvey
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Set the affinity for the pod. |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| deployment | object | `{}` |  |
| externalDatabase.database | string | `"limesurvey"` | External Database database name |
| externalDatabase.existingSecret | string | `""` | Use an existing secret for retrieving the database password. The secret must contain the field "mariadb-password" |
| externalDatabase.host | string | `"mariadb.example.com"` | External Database server host |
| externalDatabase.password | string | `""` | External Database user password |
| externalDatabase.port | int | `3306` | External Database server port |
| externalDatabase.type | string | `"mysql"` | Type of external database ("mysql" or "pgsql") |
| externalDatabase.username | string | `"limesurvey"` | External Database username |
| extraEmptyDirMounts | list | `[]` | This allows you to mount additional "emptyDirs" into the Limesurvey container |
| extraVolumeMounts | list | `[]` | This allows you to mount additional volumes into the Limesurvey container |
| fullnameOverride | string | `""` | String to override the default generated fullname |
| image.pullPolicy | string | `"IfNotPresent"` | The docker image pull policy |
| image.repository | string | `"adamzammit/limesurvey"` | The docker image repository to use |
| image.tag | string | vhart appVersion | The docker image tag to use |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` | Additional annotations |
| ingress.className | string | `""` | Specifies what type of Ingress should be created |
| ingress.enabled | bool | `false` | Specifies whether Ingress should be created or not |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` | Ingress tls |
| limesurvey.admin.email | string | `"lime@lime.lime"` | The email address of the Limesurvey administrator |
| limesurvey.admin.existingSecret | string | `""` | Use existing secret (admin.password will be ignored). secret must contain the key limesurvey-admin-password |
| limesurvey.admin.name | string | `"Lime Administrator"` | The full name of the Limesurvey administrator |
| limesurvey.admin.password | string | `""` | The password of the Limesurvey administrator |
| limesurvey.admin.username | string | `"admin"` | The username of the Limesurvey administrator) |
| limesurvey.dbSessions | string | `""` | Leave blank or don't set to use file based sessions. Set to any value to use DB based sessions |
| limesurvey.debug | string | `"0"` | Debug level of Limesurvey, 0 is off, 1 for errors, 2 for strict PHP and to be able to edit standard templates |
| limesurvey.dontShowScriptName | string | `""` | Leave blank or don't set to show the script name `index.php` in URLs. Set to any value to omit the script name |
| limesurvey.livenessProbe.enabled | bool | `true` |  |
| limesurvey.readinessProbe.enabled | bool | `true` |  |
| limesurvey.smtp.debug | string | `""` | set this to any value to enable SMTP debug mode |
| limesurvey.smtp.existingSecret | string | `""` | Use existing secret (smtp.password will be ignored). secret must contain the key limesurvey-smtp-password |
| limesurvey.smtp.from_email | string | `"your-email@example.net"` | The email address where messages will be sent from |
| limesurvey.smtp.host | string | `""` | set the SMTP host - you can also specify a different port than 25 by using this format: [hostname:port], e.g. "smtp.example.com:587") |
| limesurvey.smtp.password | string | `""` | SMTP authorization password - empty password is not allowed |
| limesurvey.smtp.ssl | string | `""` | set this to "ssl" to use SSL/TLS or "tls" to use StartTLS for SMTP connection |
| limesurvey.smtp.user | string | `""` | only set this if your server requires authorization - if you set it you HAVE to set a password too |
| limesurvey.sqlDebug | string | `"0"` | Debug level of Limesurvey for SQL, 0 is off, 1 is on - note requires LIMESURVEY_DEBUG set to 2 |
| limesurvey.tablePrefix | string | `"lime_"` | Set this to "myprefix_" if you want your table names to have the myprefix_ |
| limesurvey.tz | string | `"Europe/Berlin"` | Time zone name. If set, will configure PHP and LimeSurvey to use this time zone |
| limesurvey.useInnodb | string | `"true"` | Leave blank or don't set to use standard MyISAM database. Set to any value to use InnoDB |
| mariadb.architecture | string | `"standalone"` |  |
| mariadb.auth.database | string | `"limesurvey"` |  |
| mariadb.auth.existingSecret | string | `""` | Use existing secret (auth.rootPassword, auth.password, and auth.replicationPassword will be ignored). secret must contain the keys mariadb-root-password, mariadb-replication-password and mariadb-password |
| mariadb.auth.password | string | `"changeme"` |  |
| mariadb.auth.username | string | `"limesurvey"` |  |
| mariadb.enabled | bool | `true` | Deploy a MariaDB server |
| mariadb.primary.persistence.accessMode | string | `"ReadWriteOnce"` | Use an existing Persistent Volume Claim (must be created ahead of time) existingClaim: "" storageClass: "" |
| mariadb.primary.persistence.enabled | bool | `true` | Enable persistence using Persistent Volume Claims ref: http://kubernetes.io/docs/user-guide/persistent-volumes/ |
| mariadb.primary.persistence.size | string | `"8Gi"` |  |
| mariadb.primary.resourcesPreset | string | `"none"` | Set container resources according to one common preset (allowed values: none, nano, small, medium, large, xlarge, 2xlarge). This is ignored if primary.resources is set (primary.resources is recommended for production). More information: https://github.com/bitnami/charts/blob/main/bitnami/common/templates/_resources.tpl#L15 |
| nameOverride | string | `""` | String to override the default generated name |
| nodeSelector | object | `{}` | Set the node selector for the pod. |
| persistence.accessModes[0] | string | `"ReadWriteOnce"` |  |
| persistence.annotations."helm.sh/resource-policy" | string | `"keep"` |  |
| persistence.enabled | bool | `true` | Enable persistence using Persistent Volume Claims ref: http://kubernetes.io/docs/user-guide/persistent-volumes/ |
| persistence.existingClaim | string | `nil` |  |
| persistence.finalizers[0] | string | `"kubernetes.io/pvc-protection"` |  |
| persistence.selectorLabels | object | `{}` |  |
| persistence.size | string | `"5Gi"` |  |
| persistence.storageClass | string | `nil` |  |
| podAnnotations | object | `{}` | Annotations for the pods |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` | Numbers of replicas |
| resources | object | `{}` | Set the resources requests and limits |
| securityContext | object | `{}` |  |
| service.port | int | `80` | Default Service port |
| service.type | string | `"ClusterIP"` | Specifies what type of Service should be created |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `false` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` | Set the tolerations for the pod. |

## Source Code

* <https://github.com/area-42/helm-charts>
* <https://github.com/adamzammit/limesurvey-docker>
* <https://limesurvey.org/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Christoph Scholz | <christoph.scholz@gmail.com> | <https://github.com/ChaosKid42> |
