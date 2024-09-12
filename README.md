[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/searchhub)](https://artifacthub.io/packages/search?repo=searchhub)
# SearchHub SmartQuery and SmartSuggest Helm Charts

This repository contains the Helm charts for deploying the **SearchHub SmartQuery** module and the **SearchHub SmartSuggest**, powerful query processing and optimization and suggest tools designed to enhance search experiences.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Adding repository](#add-repo)
3. [SmartQuery](#smartquery)
   1. [Install](#smartquery-install)
   2. [Upgrading](#smartquery-upgrade)
   3. [Uninstall](#smartquery-uninstall)
   4. [Configuration](#smartquery-configuration)
4. [SmartSuggest](#smartsuggest)
   1. [Install](#smartsuggest-install)
   2. [Upgrading](#smartsuggest-upgrade)
   3. [Uninstall](#smartsuggest-uninstall)
   4. [Configuration](#smartsuggest-configuration)

## Prerequisites <a name="prerequisites"></a>

- Kubernetes 1.14+
- Helm 3.0+

## Adding the Helm Repository <a name="add-repo"></a>

To use the **SearchHub SmartQuery** or **SearchHub SmartSuggest** Helm chart, you need to add this repository to your Helm setup. Run the following command:

```bash
helm repo add searchhub https://github.com/searchhub/searchhub-helm-charts/raw/main/
helm repo update
```

## SmartQuery <a name="smartquery"></a>

### Installing the SmartQuery Chart <a name="smartquery-install"></a>
To install a release of the **SearchHub SmartQuery** module, use the following command. Replace `<release-name>` with your desired release name and `<namespace>` with the appropriate Kubernetes namespace:

```bash
helm install <release-name> searchhub/smartquery --namespace <namespace>
```

Alternatively, if you want to customize the chart, create a `values.yaml` file and install the chart with custom values, you find the default values.yaml [here](smartquery/values.yaml):

```bash
helm install <release-name> searchhub/smartquery --namespace <namespace> -f values.yaml
```

### Upgrading the SmartQuery Chart <a name="smartquery-upgrade"></a>
To upgrade an existing release to a newer version of the chart:

```bash
helm upgrade <release-name> searchhub/smartquery --namespace <namespace>
```

### Uninstalling the SmartQuery Chart <a name="smartquery-uninstall"></a>
To uninstall the release:

```bash
helm uninstall <release-name> --namespace <namespace>
```

### Configuration SmartQuery <a name="smartquery-configuration"></a>
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

## SmartSuggest <a name="smartsuggest"></a>

### Installing the SmartSuggest Chart <a name="smartsuggest-install"></a>
To install a release of the **SearchHub SmartSuggest** module, use the following command. Replace `<release-name>` with your desired release name and `<namespace>` with the appropriate Kubernetes namespace:

```bash
helm install <release-name> searchhub/smartsuggest --namespace <namespace>
```

Alternatively, if you want to customize the chart, create a `values.yaml` file and install the chart with custom values, you find the default values.yaml [here](smartsuggest/values.yaml):

```bash
helm install <release-name> searchhub/smartsuggest --namespace <namespace> -f values.yaml
```

### Upgrading the SmartSuggest Chart <a name="smartsuggest-upgrade"></a>
To upgrade an existing release to a newer version of the chart:

```bash
helm upgrade <release-name> searchhub/smartsuggest --namespace <namespace>
```

### Uninstalling the SmartSuggest Chart <a name="smartsuggest-uninstall"></a>
To uninstall the release:

```bash
helm uninstall <release-name> --namespace <namespace>
```

### Configuration SmartSuggest <a name="smartsuggest-configuration"></a>
You can customize the deployment using the `values.yaml` file. The following is a sample of customizable parameters:

```yaml
replicaCount: 2
image:
  repository: your-repo/smartsuggest
  tag: latest
  pullPolicy: IfNotPresent
env:
  - name: SH_API_KEY
    value: "<YourS3cr3tAPIkey>"
  - name: SH_INIT_TENANTS
    value: "example.num1,example.num2"
  - name: JAVA_OPTS
    value: "-Dsmartquery.updateRateInSeconds=60"
resources:
  limits:
    cpu: "1"
    memory: 1Gi
  requests:
    cpu: 750m
    memory: 1Gi
```
For a full list of configurable parameters, see the [smartsuggest/values.yaml](smartsuggest/values.yaml) file in this repository.
