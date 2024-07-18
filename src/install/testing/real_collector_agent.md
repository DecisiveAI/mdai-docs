# Using a real agent/collector to send data to MDAI Cluster

>Visit the [OTel Collector Docs site](https://opentelemetry.io/docs/collector/configuration/) to learn more about configuring your collector based on your specific data sources and destinations.

## General setup and connectivity from collector to MDAI

1. Determine which sources of data (collector/agent) you'd like to point at your MDAI Cluster instance.
2. Use your CNAME (from your host provider) or DNS (from AWS LB) as mentioned in our [Ingress documentation](../../advanced/ingress.md).
3. Configure your agent/collector to point to the CNAME or DNS as mentioned in our [Ingress documentation](../../advanced/ingress.md).
4. SEE RESULTS! [Verify data flow](./verify.md)

### Where can I find my ingress endpoint?

The `External-IP` for the `gateway-collector` from the following command. You will need this to send telemetry from your agents/collectors of choice. Run the following command from your terminal to access the External-IP for configuring your agents to use.

```bash
kubectl get svc gateway-collector -n default
```

### Examples coming soon

While we know these docs will help guide you to the right configuration, we understand you might need further help. We're actively working on examples connecting commonly used collectors/agents to an MDAI Cluster. 

If you have special requests for how-to-guides..
* Email us at <a href="mailto:support@mydecisive.ai" target="_blank">support@mydecisive.ai</a>
* File an issue under the <a href="https://github.com/DecisiveAI/mdai-inkops/issues/new" target="_blank">MDAI InkOps Project

----
<span class="left"><a href="../installation.md">⏪ Back to Intro: Generate and Receive Telemetry</a></span>
<span class="right"><a href="./telemetrygen.md">Next Step: TelemetryGen ⏩</a></span>