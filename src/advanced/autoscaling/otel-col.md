# AutoScaling

## OpenTelemetry Collector

We have built an HPA config for one of our cluster's core components, the OTel collector app (`lib/mdai-operator.yaml`) with the following settings:

```yaml
# 2 replicas recommnded
replicas: 2
# mandatory only when  autoscaler is enabled
# otherwise optional. can be used to limit resources consumtion
resources:
  limits:
    cpu: 500m
    memory: 500Mi
  requests:
    cpu: 250m
    memory: 250Mi
```

<div class="warning">
  <em><b>Note</b>: If you decide to change these settings, it is possible that operations and performance of the OTel collector and cluster may become sub-optimal. We've tested with this configuration and cannot guarantee performance outside of these bounds.</em>
</div>

### Benchmarking - Plans for the future!

We are working hard to understand and create multiple configurations that are resource and cost-effective under predictable and variable workload demands.

We will soon publish a report of the current constraints we are using for testing the above configuration, as well as others.

## Other Cluster Components

📺  **Coming soon! Stay tuned!**  📺

We will shortly begin work on optimizing HPA (or any other scaling method) for both the following components pending community feedback
1. MDAI Console 
2. Datalyzer module 

## Have some recommendations for where we should spend our energy?

Are you experiencing any pain using the MDAI Cluster? Do you have specific configurations or workload demands you'd like us to help test?
* Email us at <a href="mailto:support@mydecisive.ai" target="_blank">support@mydecisive.ai</a>
* File an issue under the <a href="https://github.com/DecisiveAI/mdai-inkops/issues/new" target="_blank">MDAI InkOps Project

<br />

----
<span class="left"><a href="../../install/installation.md">⏪ Back to: Installation</a></span>
<span class="right"><a href="../console/mdai-console.md">Next up: MDAI Console Usage ⏭️</a></span>
