# Node AutoScaling

## Karpenter NodePool Settings

The following configuration is used for Karpenter to properly autoscale the EC2 Nodes that your Cluster runs on.

```yaml
apiVersion: karpenter.sh/v1beta1
kind: NodePool
metadata:
  name: default
spec:
  template:
    spec:
      requirements:
        - key: kubernetes.io/arch
          operator: In
          values: ["amd64"]
        - key: kubernetes.io/os
          operator: In
          values: ["linux"]
        - key: karpenter.sh/capacity-type
          operator: In
          values: ["on-demand"]
        - key: karpenter.k8s.aws/instance-category
          operator: In
          values: ["t"]
        - key: karpenter.k8s.aws/instance-family
          operator: In
          values: ["t2"]
        - key: node.kubernetes.io/instance-type
          operator: In
          values: ["t2.micro"]
      nodeClassRef:
        apiVersion: karpenter.k8s.aws/v1beta1
        kind: EC2NodeClass
        name: default
  limits:
    cpu: 1000
  disruption:
    consolidationPolicy: WhenUnderutilized
    expireAfter: 720h # 30 * 24h = 720h
```

<div class="warning">
  <em><b>Note</b>: If you decide to change these settings, it is possible that operations and performance of your Cluster may become sub-optimal. We've tested with this configuration and cannot guarantee performance outside of these bounds.</em>
</div>

### Benchmarking - Plans for the future!

We are working hard to understand and create multiple configurations that are resource and cost-effective under predictable and variable workload demands.

We will soon publish a report of the current constraints we are using for testing the above configuration, as well as others.

## Have some recommendations for where we should spend our energy?

Are you experiencing any pain using the MDAI Cluster? Do you have specific configurations or workload demands you'd like us to help test?
* Email us at <a href="mailto:support@mydecisive.ai" target="_blank">support@mydecisive.ai</a>
* File an issue under the <a href="https://github.com/DecisiveAI/mdai-inkops/issues/new" target="_blank">MDAI InkOps Project

<br />

----
<span class="left"><a href="./installation.md">⏪ Back to: Installation</a></span>
<span class="right"><a href="../console/mdai-console.md">Next up: MDAI Console Usage ⏭️</a></span>
