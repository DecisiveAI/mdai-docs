# Source Attribution

<!-- toc -->

## What is it?

Different services, applications, hosts and other parts of your software estate emit telemetry differently, and the Source Attribution Module in the MDAI Cluster can help you see which services are sending the most telemetry data, and potentially costing the most to store that telemetry data.

The OpenTelemetry collector provides _counts_ per telemetry type (metrics, logs, and traces) out of the box, but does not measure size (in bytes) of this data. The MDAI Cluster Source Attribution Module measures telemetry separately from the collector to alleviate the computational burden of those calculations, but still does so within the Cluster to minimize data transmission costs or security concerns.

<div  style="text-align: center;">
  <a href="../../media/service-attribution-screenshot.png" style="cursor: zoom-in;">
    <img style="width: 400px;" src="../../media/service-attribution-screenshot.png" alt="Source attribution module diagram" />
  </a>
</div>
<p style="text-align: center;">
  <em>The MDAI Console displaying per-service Telemetry measures for the OpenTelemetry Demo</em>
</p>

## How do I use it?

You can use the MDAI CLI to easily enable or disable the Source Attribution feature in your MDAI Cluster, or you can edit your collector resource manually if you prefer.

### MDAI CLI

#### Enable

```sh
mdai enable --module datalyzer
```

#### Disable

```sh
mdai disable --module datalyzer
```

### Manually update k8s Collector Resource

Get the custom resource for your collector:

```sh
kubectl get mydecisiveengine  mydecisiveengine-sample --namespace mdai-otel-nucleus -o yaml > cr.yml
```

Edit the `cr.yml` to change the `spec.telemetryModule.collectors[0].measureVolumes` to `true` or `false` depending on whether you want the Source Attribution feature enabled or not.

## How does it work?

### Components of the Source Attribution Module:

- The Datalyzer, a lightweight OTLP service that measures Telemetry data on a per-service basis, completely within your cluster
- The MDAI Operator, which directs data from your Telemetry pipelines to the Datalyzer for measurement
- The MDAI Console Analysis View, which displays per-service telemetry measurements and the ratio of outgoing to incoming data.

<div  style="text-align: center;">
  <a href="../../media/service-attribution.png" style="cursor: zoom-in;">
    <img style="width: 400px;" src="../../media/service-attribution.png" alt="Source attribution module diagram" />
  </a>
</div>
<p style="text-align: center;">
  <em>The Datalyzer Service measures telemetry data per-source</em>
</p>