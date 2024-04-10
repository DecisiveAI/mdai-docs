# Destroy MDAI Engine

When decommissioning a cluster or performing a clean-up operation, you need to delete all resources and configurations.


## How to Destroy

1. Delete all artifacts associated with the cluster using `kubectl delete -f cluster-manifests/`.
2. Confirm the deletion of pods, services, deployments, and other resources, effectively destroying the Kubernetes cluster.


### Data Persistence - Prometheus
