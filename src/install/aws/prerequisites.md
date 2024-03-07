## Prerequisites

### System Requirements

Make sure that your developer environment has the following. This page assumes that you’re using bash. Adapt configuration and commands as necessary for your preferred shell.

- Install [Go](https://go.dev/dl/) (1.20 or higher) from source or use homebrew `brew install go`
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:
```
export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
```
- Install [node](https://nodejs.org/en/download).

### AWS Requirements

- Install [AWS CDK Toolkit](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install)
- Install [AWS SSO](https://docs.aws.amazon.com/cli/latest/userguide/sso-configure-profile-token.html)
