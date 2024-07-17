# Semi-Automated installation
----
## Check us out!

First things first, you have to check out our [MDAI infrastructure installation repo](https://github.com/DecisiveAI/mdai-inkops).

```shell
git clone https://github.com/DecisiveAI/mdai-inkops.git
```

## Prerequisites

As mentioned, the only manual step for this install method is to enable you to have full visibility and control of your system dependencies.

- Install [Go](https://go.dev/dl/) (1.20 or higher).
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:

 ```shell
 export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
 ```

- Install [node](https://nodejs.org/en/download)
- Install [docker](https://www.docker.com/get-started/)
- Install [helm](https://helm.sh/docs/intro/install/)
- Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) for local cluster management using docker containers

## Install Commands

```shell
make -f ./make/Makefile-local-recipes create-mdai-semi-auto
```

>_Note: Once the MDAI Cluster installed your k8s context will be switched automatically to new cluster._

<div class="warning">
  <b>Troubleshooting</b><br /><br />
  You may run into an error running this command related to the docker daemon. Please see our <a href="../../troubleshooting.md#docker-daemon-not-started" target="_blank">Troubleshooting Guide</a> to see if this issues is relevant to you and how to resolve it. 
</div>

<br />

----

<span class="left"><a href="./install.md">⏪ Back to Install</a></span>
<span class="right"><a href="./configure.md">Next Step: Configure ⏩</a></span>