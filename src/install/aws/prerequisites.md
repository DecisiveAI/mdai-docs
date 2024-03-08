## Prerequisites

### System Requirements

Ensure your development environment has access to all of the following software and settings.

**Note:** *This page assumes you’re using bash, but you can modify these configurations and commands as needed for your preferred command line interface.*

- Install [Go](https://go.dev/dl/) (1.20 or higher) from source or use homebrew `brew install go`
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:
```
export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
```
- Install [node](https://nodejs.org/en/download).

### AWS Requirements

- Install [AWS CDK Toolkit](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install)
- Install [AWS SSO](https://docs.aws.amazon.com/cli/latest/userguide/sso-configure-profile-token.html)

<br />

----

<p style="text-align: center;">
  <a href="./start.md">Back to Getting Started</a>
</p>
<p style="text-align: center;">
  <a href="./aws-sso.md">Next Step: Configure AWS SSO >></a>
</p>
