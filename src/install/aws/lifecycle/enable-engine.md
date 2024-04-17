# Enable Engine Ingress

After completing any tasks related to disabling your MDAI Engine instance (i.e., maintenance or engine data flow resolution), you likely want to resume ingress and ensure that data flow resumes smoothly.

## How to Enable...

### Manual

- Set replica count to `2` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 2
```
- Apply config to cluster

<!-- this doesn't work - must fix -->
`kubectl apply -f values/params-values-otel.yaml`


### Automated

Check back soon, we're working on an automated flow for disabling your engine.

<!--
1. Apply the configuration to enable ingress using `kubectl apply -f enable-ingress.yaml`.
2. Verify that incoming traffic reaches the cluster again, confirming that data flow has been re-instantiated.  -->

<br />

----
<span class="left"><a href="./disable-engine.md">⏪ Back to: Disable Engine </a></span>
<span class="right"><a href="./destroy-engine.md">Next Step: Destroy Engine  ⏩</a></span>
