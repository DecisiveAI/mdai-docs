# Quick Start Guide

## Setup the MDAI Engine© locally

You are going to learn to do the following in less than five minutes:
* Set up and run a local instance of MDAI Engine©
* Send telemetry to the MDAI Engine©
* Use the MDAI Engine Console© to verify data flowing through the MDAI Engine©.

## Prerequisites

Make sure that your developer environment has the following. This page assumes that you’re using bash. Adapt configuration and commands as necessary for your preferred shell.

* Install [Go](https://go.dev/dl/) (1.20 or higher) from source or use homebrew  `brew install go`
* [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:
```
export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
```
* Install [npm](https://nodejs.org/en/download) from source or use homebrew  `brew install npm`
* Install [aws-cdk](https://docs.aws.amazon.com/cdk/v2/guide/cli.html) from source or use homebrew  `brew install aws-cdk`. AWS CDK (requires Node.js ≥ 14.15.0)
* Install [minikube](https://minikube.sigs.k8s.io/docs/start/).


## Setup Environment
1. Create a cluster where the Engine can be installed. For our example, we'll use minikube.
```@bash
minikube start
```

2. Setup and configure a local instance of the MDAI Engine©

```@bash
make local-deploy
```

## Generate and Collect telemetry

## Next steps
