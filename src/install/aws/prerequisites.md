# AWS Install Prerequisites
____
### System Requirements

Ensure your development environment has access to all of the following software and settings.

**Note:** *This page assumes you’re using bash, but you can modify these configurations and commands as needed for your preferred command line interface.*

- Install [Go](https://go.dev/dl/) (1.20 or higher) from source or use homebrew `brew install go`
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:
```
export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
```
- Install [node](https://nodejs.org/en/download).

>**Note:** We do install Helm automatically, however, it's important to note that we support [Helm v3.13.0](https://github.com/helm/helm/releases/tag/v3.13.0) and later. If you have helm installed, but at an earlier version, we cannot guarantee our install process will work as expected.

### AWS Requirements

- Install [AWS CDK Toolkit](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install)
- Install [AWS SSO](https://docs.aws.amazon.com/cli/latest/userguide/sso-configure-profile-token.html)

### User Requirements

We never desire to exclude anyone from using our solutions. Instead we encourage and inspire you to obtain an intermediate knowledge of AWS (or a ton of grit) before continuing with this install. Here's a great [AWS Training](https://aws.amazon.com/training/) resource!

<br />

----
<span class="left"><a href="./start.md">⏪ Back to: Getting Started</a></span>
<span class="right"><a href="./aws-sso.md">Next Step: Configure AWS SSO ⏩</a></span>

