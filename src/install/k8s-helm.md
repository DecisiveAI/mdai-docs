# Deploy the MyDecisive Engine Helm chart

You may deploy [the MyDecisive Engine Helm Chart](#) directly to an existing Kubernetes cluster

## Prerequisites

- A Kubernetes cluster you have admin access to, and can deploy Helm charts to
- `kubectl` and `helm` installed on the deploying machine

## Install Steps

1. Run this command to add the chart repository to your repository list:

```shell
helm repo add mydecisive TODO FILL THIS IN
```

2. Run this command to add the chart repository to your repository list:

```shell
helm install mydecisive-engine mydecisive/engine
```

3. Verify the engine is up and running by (SOMETHING SOMETHING FILL THIS IN)

## Uninstallation

To remove the MyDecisive Engine from your k8s cluster, run the following:

```shell
helm uninstall chart mydecisive-engine
```
