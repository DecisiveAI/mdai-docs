# Semi-Automated installation
----

## Additional Prerequisites

As mentioned, the only manual step for this install method is to enable you to have full visibility and control of your system dependencies.

- Install [Go](https://go.dev/dl/) (1.20 or higher).
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:

 ```shell
 export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
 ```

- Install [npm](https://nodejs.org/en/download)
- Install [aws-cdk](https://docs.aws.amazon.com/cdk/v2/guide/cli.html)
- Install [docker](https://www.docker.com/get-started/)
- Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) for local cluster management using docker containers

## Install Commands

```shell
make -f ./make/Makefile-local-recipes create-mdai-semi-auto
```

<br />

----

  <span class="left"><a href="./install.md">⏪ Back to Install</a></span>
  <span class="right"><a href="./automated-install.md">Next Step: Automated Install ⏩</a></span>
