# Quick Start Guide

<!-- toc -->

## Setup the MDAI Engine™ locally

You are going to learn to do the following in less than five minutes:

- Set up and run a local instance of MDAI Engine™
- Send telemetry to the MDAI Engine™
- Access MDAI Engine Console™ to verify data flowing through the MDAI Engine™.

## Prerequisites

### Automated pre-req installations

1. Pull down the latest from the [MDAI infrastructure installation repo](https://github.com/DecisiveAI/decisive-engine-aws-cdk)
2. Run automated installation script
   > ```@bash
   > make install-local-dependencies
   > ```

### Manual pre-req installations

- Install [Go](https://go.dev/dl/) (1.20 or higher).
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:
  > ```@bash
  > export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
  > ```
- Install [npm](https://nodejs.org/en/download)
- Install [aws-cdk](https://docs.aws.amazon.com/cdk/v2/guide/cli.html)
- Install [docker](https://www.docker.com/get-started/)
- Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) for local cluster management using docker containers

## Setup Environment

1. Create a cluster where the Engine can be installed. For our example, we'll use kind.
   > ```@bash
   > <!--  Create cluster -->
   > kind create cluster --name mdai-local
   >
   > <!-- Check that your cluster is up and running -->
   > kind get clusters
   > ```
2. Setup and configure a local instance of the MDAI Engine™

   > ````@bash
   > make local-deploy
   > ```kubectl-config
   > ````

3. Ensure your cluster is up and running.

   > ```@bash
   > kubectl get pods
   > ```
   >
   > _Note: the pod that starts with `mydecisive-engine-ui-_`\*

4. Enable port forwarding from cluster to localhost

   > ```
   > <!-- Example kubectl port-forward mydecisive-engine-ui-578f644b7-k9q47 5173:5173 -->
   >
   > kubectl port-forward <POD_NAME> <PORT>:<PORT>
   > ```

5. View the MDAI Console at [http://localhost:5173](localhost:5173) 🐙🎉

![A bright and shiny MDAI Engine™ Console](../media/console-new-and-shiny.png)

## Generate and Collect telemetry

1. Install OpenTelemetry's [telemetrygen](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/cmd/telemetrygen) utility.
   > ```@bash
   > go install github.com/open-telemetry/opentelemetry-collector-contrib/cmd/telemetrygen@latest
   > ```
2. Send Telemetry to the collector
   > ```@bash
   > $GOBIN/telemetrygen traces --otlp-insecure --traces 3
   > ```
3. _Optional: Add a cronjob to schedule telemetry at a cadence_
   > ```
   > TODO: command goes here!
   > ```

## Validate data flow

1. View the [local MDAI console](localhost:5173)
2. As telemetry flows through the engine, you will see counts increase in the console, color-coded by telemetry type. 🐙🎉

![The MDAI Engine™ Console showing data flows](../media/console-data-flow.png)

> Note: Data flowing to `debug` exporters are not counted towards data flow totals in the right sidebar

## Next steps
