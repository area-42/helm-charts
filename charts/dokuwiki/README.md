# DokuWiki

![Version: 0.1.6](https://img.shields.io/badge/Version-0.1.6-informational?style=for-the-badge)
![Type: application](https://img.shields.io/badge/Type-application-informational?style=for-the-badge)
![AppVersion: 2025-05-14a](https://img.shields.io/badge/AppVersion-2025--05--14a-informational?style=for-the-badge)

## Description

The OpenSource Wiki Software. This chart uses the official Docker image for DokuWiki.

## Usage

```console
helm repo add area-42 https://area-42.github.io/helm-charts
helm repo update

helm install dokuwiki area-42/dokuwiki
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
| dokuwiki.admin.memoryLimit | string | `"256M"` | Process Memory Limit |
| dokuwiki.admin.timezone | string | `"UTC"` | The timezone |
| dokuwiki.admin.uploadLimit | string | `"128M"` | File upload size limit |
| dokuwiki.livenessProbe | object | See _values.yaml_ | Liveness probe configuration for the default container. |
| dokuwiki.readinessProbe | object | See _values.yaml_ | Readiness probe configuration for the default container. |
| extraContainers | list | `[]` | This allows you to add additional containers (sidecars) to the DokuWiki container |
| extraEmptyDirMounts | list | `[]` | This allows you to mount additional "emptyDirs" into the DokuWiki container |
| extraVolumeMounts | list | `[]` | This allows you to mount additional volumes into the DokuWiki container |
| fullnameOverride | string | `""` | String to override the default generated fullname |
| global.imageRegistry | string | `""` | Overrides the Docker registry globally for all images |
| image.pullPolicy | string | `"IfNotPresent"` | The docker image pull policy |
| image.repository | string | `"dokuwiki/dokuwiki"` | The docker image repository to use |
| image.tag | string | vhart appVersion | The docker image tag to use |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` | Additional annotations |
| ingress.className | string | `""` | Specifies what type of Ingress should be created |
| ingress.enabled | bool | `false` | Specifies whether Ingress should be created or not |
| ingress.extraTls | list | `[]` | Additional definitions for ingress tls |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` | Ingress tls |
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
* <https://github.com/dokuwiki/docker>
* <https://www.dokuwiki.org/dokuwiki>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Christoph Scholz | <christoph.scholz@gmail.com> | <https://github.com/ChaosKid42> |
