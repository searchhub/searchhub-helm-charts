[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/searchhub)](https://artifacthub.io/packages/search?repo=searchhub)
# SearchHub SmartQuery Helm Chart

This repository contains the Helm chart for deploying the **SearchHub SmartQuery** module, a powerful query processing and optimization tool designed to enhance search experiences.

## Prerequisites

- Kubernetes 1.14+
- Helm 3.0+

## Adding the Helm Repository

To use the **SearchHub SmartQuery** Helm chart, you need to add this repository to your Helm setup. Run the following command:

```bash
helm repo add searchhub https://github.com/searchhub/searchhub-helm-charts/raw/main/
helm repo update
```

## Installing the SmartQuery Chart
To install a release of the **SearchHub SmartQuery** module, use the following command. Replace `<release-name>` with your desired release name and `<namespace>` with the appropriate Kubernetes namespace:

```bash
helm install <release-name> searchhub/smartquery --namespace <namespace>
```

Alternatively, if you want to customize the chart, create a `values.yaml` file and install the chart with custom values, you find the default values.yaml [here](smartquery/values.yaml):

```bash
helm install <release-name> searchhub/smartquery --namespace <namespace> -f values.yaml
```

## Upgrading the Chart
To upgrade an existing release to a newer version of the chart:

```bash
helm upgrade <release-name> searchhub/smartquery --namespace <namespace>
```

## Uninstalling the Chart
To uninstall the release:

```bash
helm uninstall <release-name> --namespace <namespace>
```

## Configuration
You can customize the deployment using the `values.yaml` file. The following is a sample of customizable parameters:

```yaml
replicaCount: 2
image:
  repository: your-repo/smartquery
  tag: latest
  pullPolicy: IfNotPresent
env:
  - name: SH_API_KEY
    value: "<YourS3cr3tAPIkey>"
  - name: SH_INIT_TENANTS
    value: "example.num1,example.num2"
resources:
  limits:
    cpu: "1"
    memory: 1Gi
  requests:
    cpu: 750m
    memory: 1Gi
```
For a full list of configurable parameters, see the [smartquery/values.yaml](smartquery/values.yaml) file in this repository.
