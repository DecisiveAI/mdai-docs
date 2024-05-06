# Uninstall the nucleus
----
Tired of using the MDAI Nucleus locally? 😭 We're sorry to see you go, but we understand.

If you have feedback for us, please let us know why!
1. [Support team email](mailto:support@mydecisive.ai)
2. [Feedback form](https://docs.google.com/forms/d/e/1FAIpQLScZNGgu5Cshd-WP7HGcvW4yPVP_NbWswcAU6vKgUnRb_6umpA/viewform?usp=sharing)


## Automated uninstall

When decommissioning a cluster or performing a clean-up operation, you need to delete all resources and configurations. Follow the steps below to uninstall your local MDAI Nucleus.

### Ensure you have the correct k8s context selected.

Make sure your k8s context is set to `kind-mdai-local` cluster:

```shell
kubectl config get-contexts
```

Switch the context if needed:

```shell
kubectl cluster-info --context kind-mdai-local
```

### Uninstall Cluster

Run automated de-installation script

```shell
 make -f ./make/Makefile-local-recipes delete-mdai
```

<!--
TODO: make a manifest for an automated flow

### Automated

1. Delete all artifacts associated with the cluster using `kubectl delete -f cluster-manifests/`.
2. Confirm the deletion of pods, services, deployments, and other resources, effectively destroying the Kubernetes cluster.
-->


### Optional: Uninstall all helm artifacts

If you want to remove all helm artifacts installed (you don't use it your other local setup), run the following

```shell
 make -f ./make/Makefile-local-recipes delete-mdai-all
```

### Data Persistence - Prometheus

<div class="warning">
  <p>
    Currently, there is no data persistence for Prometheus. If you destroy your nucleus, you'll also be destroying your prometheus instance and all associated data. 🪦
  </p>
  <p>
    Until MDAI is able to support a more robust persistence layer or snapshot capability, we recommend using a <a href="https://prometheus.io/docs/prometheus/latest/storage/#remote-storage-integrations" target="_blank">remote storage option</a> for your persistence needs.
  </p>
</div>

<br />

----
<span class="left"><a href="./enable-nucleus.md">⏪ Back to: Enable Nucleus</a></span>
<span class="right"><a href="../../congrats.md">Next Step: Congrats ⏩</a></span>
