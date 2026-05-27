# Base Cron Job Chart

Our base chart is an open source project, initiated for creating base deployment templates in our common cron and cron job services. It can be used for any basic application you want to deploy over Kubernetes. Just customize with your purpose, and run it!

## TL;DR

```bash
$ helm repo add 99group https://urbanindo.github.io/99-charts
$ helm install myrelease 99group/base-job
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
$ helm install my-release 99group/base-job
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