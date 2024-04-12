# Disable Engine Ingress

You may need to temporarily halt incoming traffic to perform maintenance or troubleshoot issues without impacting data flow.

## How to Disable

### Manual

- Set replica count to `0` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 0
```
- Apply config to cluster

<!-- this doesn't work - must fix -->
`kubectl apply -f values/params-values-otel.yaml`

<!--
TODO: make a target for an automated flow

### Automated

1. Apply the configuration to disable ingress using `kubectl apply -f disable-ingress.yaml`.
2. Verify that incoming traffic no longer reaches the cluster, confirming that data flow has stopped. -->

----
<span class="left"><a href="./overview.md">⏪ Back to: Lifecycle Management Overview</a></span>
<span class="right"><a href="./enable-engine.md">Next Step:  Enable Engine ⏩</a></span>
