# Base Chart

Our base chart is an open source project, initiated for creating base deployment templates in our common services. It can be used for any basic application you want to deploy over Kubernetes. Just customize with your purpose, and run it!

## TL;DR

```bash
$ helm repo add 99group https://urbanindo.github.io/99-charts
$ helm install myrelease 99group/base
```

## Introduction

[99 Group] (https://99.co) Engineers carefully design charts, are actively maintained, and are one of our company's standard ways to deploy services to Kubernetes Clusters.
We are constantly improvising on each of our open source projects, so we look forward to user feedback on using this chart. We will be very happy if we continue to make improvements and add features in the future to make your work easier.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.1.0

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm repo add 99group https://urbanindo.github.io/99-charts
$ helm install my-release 99group/base
```

These commands deploy our base chart on the Kubernetes cluster in the default configuration.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

### Common parameters

| Name                | Description                                                                           | Value           |
| ------------------- | ------------------------------------------------------------------------------------- | --------------- |
| `nameOverride`      | String to partially override image.fullname template (will maintain the release name) | `""`            |
| `fullnameOverride`  | String to fully override image.fullname template                                      | `""`            |


### Image parameters

| Name                 | Description                                                          | Value                  |
| -------------------- | -------------------------------------------------------------------- | ---------------------- |
| `image.repository`   | Source image repository, you can add fullpath of image                                               | `nginx`        |
| `image.tag`          | Source image tag (immutable tags are recommended)                     | `latest` |
| `image.pullPolicy`   | Source image pull policy                                              | `IfNotPresent`         |
| `imagePullSecrets`  | Specify docker-registry secret names as an array                     | `[]`                   |


### Deployment parameters

| Name                                    | Description                                                                               | Value   |
| --------------------------------------- | ----------------------------------------------------------------------------------------- | ------- |
| `replicaCount`                          | Number of replicas to deploy                                                        | `1`     |
| `configmap.enabled`                          | Enable configmap                                                        | `false`     |
| `configmap.name`                          | Set configmap name                                                        | `demo`     |
| `podAnnotations`                        | Annotations for Deployment pods                                                                | `{}`    |
| `SecurityContext.capabilities`      | Enabled Security Context with some capabilities                                           | `true` |
| `SecurityContext.readOnlyRootFilesystem`    | Set Security Context readOnlyRootFilesystem                                     | `true`  |
| `SecurityContext.runAsUser`    | Set Security Context runAsUser                                     | `1001`  |
| `SecurityContext.runAsNonRoot` | Set Security Context runAsNonRoot                                  | `true`  |
| `resources.limits`                      | The resources limits for the container                                              | `{}`    |
| `resources.requests`                    | The requested resources for the container                                           | `{}`    |
| `autoscaling.enabled`                   | Enable autoscaling for deployment                                                   | `false` |
| `autoscaling.minReplicas`               | Minimum number of replicas to scale back                                                  | `""`    |
| `autoscaling.maxReplicas`               | Maximum number of replicas to scale out                                                   | `""`    |
| `autoscaling.targetCPU`                 | Target CPU utilization percentage                                                         | `""`    |
| `autoscaling.targetMemory`              | Target Memory utilization percentage                                                      | `""`    |
| `hpaAnnotations.enabled`              | Enabling hpa annotations                                                      | `""`    |
| `hpaAnnotations.prometheusServer`              | Set destination prometheus server                                                      | `""`    |
| `livenessCheck.enabled`                 | Enable livenessProbe                                                                      | `true`  |
| `livenessProbe.initialDelaySeconds`     | Initial delay seconds for livenessProbe                                                   | `30`    |
| `livenessProbe.periodSeconds`           | Period seconds for livenessProbe                                                          | `10`    |
| `livenessProbe.timeoutSeconds`          | Timeout seconds for livenessProbe                                                         | `5`     |
| `livenessProbe.failureThreshold`        | Failure threshold for livenessProbe                                                       | `6`     |
| `livenessProbe.successThreshold`        | Success threshold for livenessProbe                                                       | `1`     |
| `readinessCheck.enabled`                | Enable readinessProbe                                                                     | `true`  |
| `readinessProbe.initialDelaySeconds`    | Initial delay seconds for readinessProbe                                                  | `5`     |
| `readinessProbe.periodSeconds`          | Period seconds for readinessProbe                                                         | `5`     |
| `readinessProbe.timeoutSeconds`         | Timeout seconds for readinessProbe                                                        | `3`     |
| `readinessProbe.failureThreshold`       | Failure threshold for readinessProbe                                                      | `3`     |
| `readinessProbe.successThreshold`       | Success threshold for readinessProbe                                                      | `1`     |
| `serviceAccount.create`                 | Enable creation of ServiceAccount for pod                                           | `false` |
| `serviceAccount.name`                   | The name of the ServiceAccount to use.                                                    | `""`    |
| `serviceAccount.annotations`            | Annotations for service account. Evaluated as a template.                                 | `{}`    |
| `nodeSelector`                          | Node labels for pod assignment. Evaluated as a template.                                  | `{}`    |
| `tolerations`                           | Tolerations for pod assignment. Evaluated as a template.                                  | `{}`    |
| `affinity`                              | Affinity for pod assignment                                                               | `{}`    |

### Traffic Exposure parameters

| Name                            | Description                                                                                            | Value                    |
| ------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------ |
| `service.type`                  | Service type                                                                                           | `ClusterIP`           |
| `service.srcPort`                  | Service Container source port                                                                                      | `80`                     |
| `service.dstPort`             | Destination service expose port                                                                                     | `80`                    |
| `virtualService.enabled`             | Enable virtual service                                                                                     | `true`                    |
| `destinationRule.enabled`             | Enable destination rule                                                                                     | `true`                    |
| `ingress.enabled`               | Set to true to enable ingress record generation                                                        | `false`                  |
| `ingress.className`               | Set class name for ingress                                                        | `""`                  |
| `ingress.annotations`           | Ingress annotations                                                                                    | `{}`                     |
| `ingress.hosts`              | Default host for the ingress resource                                                                  | `[]`            |
| `ingress.tls`                   | Create TLS Secret                                                                                      | `[]`                  |
|



Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install my-release \
  --set imagePullPolicy=Always \
    99group/base
```

The above command sets the `imagePullPolicy` to `Always`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install my-release -f values.yaml 99group/base
```

> **Tip**: You can use the default [values.yaml](values.yaml)


## Troubleshooting

Find more information about how to deal with common errors related to 99 Group Helm charts in [this troubleshooting guide](https://docs.99.co/engineer/how-to/troubleshoot-helm-chart-issues).