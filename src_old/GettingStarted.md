# MyDecisive Engine

## Getting Started with the MyDecisive Engine

### Prerequisites
The Decisive Engine requires the following components to be present to be able to operate:

1. A Kubernetes (k8s) cluster that you have administrative access to
   - If you do not currently have a cluster, or need to create a new one, please follow [the k8s setup guide](./K8sSetup.md) before continuing.
1. One or more systems that have (A) an OpenTelemetry agent installed, (B) are capable of emitting OpenTelemetry Protocol (OTLP) Telemetry, or (C) are capable of sending data via OpenTelemetry-Collector-compatible protocol to send data to the engine
1. One or more OpenTelemetry-Collector-compatible backends to accept the data emitted by the engine
