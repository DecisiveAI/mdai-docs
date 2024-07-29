# Source Attribution

## What is it?

Different services, applications, hosts and other parts of your software estate emit telemetry differently, and the Source Attribution Module in the MDAI Cluster can help you see which services are sending the most telemetry data, and potentially costing the most to store that telemetry data.

<div  style="text-align: center;">
<a href="../../media/service-attribution.png" style="cursor: zoom-in;">
<img style="width: 400px;" src="../../media/service-attribution.png" alt="Source attribution module diagram" />
</a>
</div>
<p style="text-align: center;">
  <em>The Datalyzer Service measures telemetry data per-source</em>
</p>

### Components of the Source Attribution Module:

- The Datalyzer, a lightweight OTLP service that measures Telemetry data on a per-service basis, completely within your cluster
- The MDAI Operator, which directs data from your Telemetry pipelines to the Datalyzer for measurement
- The MDAI Console Analysis View, which displays per-service telemetry measurements and the ratio of outgoing to incoming data.

<div  style="text-align: center;">
<a href="../../media/service-attribution-screenshot.png" style="cursor: zoom-in;">
<img style="width: 400px;" src="../../media/service-attribution-screenshot.png" alt="Source attribution module diagram" />
</a>
</div>
<p style="text-align: center;">
  <em>The MDAI Console displaying per-service Telemetry measures for the OpenTelemetry Demo</em>
</p>

## How to enable

### MDAI CLI

### k8s

## How to disable

### MDAI CLI

### k8s
