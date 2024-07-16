# Automated installation
----

Our automated installation process is setting up all the required dependencies like
- Docker
- Kind cluster
- Node
- Go
- Helm (we support [Helm v3.13.0](https://github.com/helm/helm/releases/tag/v3.13.0) and later)

Here are installation steps:

- Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) for local cluster management using docker containers
- Run automated installation script

```shell
make -f ./make/Makefile-local-recipes create-mdai
```

>_Note: Once the MDAI Cluster installed your k8s context will be switched automatically to new cluster._

<div class="warning">
  <b>Troubleshooting</b><br /><br />
  You may run into an error running this command related to the docker daemon. Please see our <a href="../../troubleshooting.md#docker-daemon-not-started" target="_blank">Troubleshooting Guide</a> to see if this issues is relevant to you and how to resolve it. 
</div>

<br />

----

<span class="left"><a href="./semiautomated-install.md">⏪ Back to Semi-Automated Install</a></span>
<span class="right"><a href="./verify.md">Next Step: Verify ⏩</a></span>
