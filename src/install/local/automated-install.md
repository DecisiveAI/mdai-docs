# Automated installation
----

Our automated installation process is setting up all the required dependencies like
- Docker
- Kind cluster
- Npm
- Aws CDK
- Go
- Helm (we support [Helm v3.13.0](https://github.com/helm/helm/releases/tag/v3.13.0) and later)

Here are installation steps:

- Git Clone to a local folder [MDAI infrastructure installation repo](https://github.com/DecisiveAI/mdai-inkops)
- Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) for local cluster management using docker containers
   - if you have brew installed: `brew install kind`
- Run automated installation script
```bash
make -f ./make/Makefile-local-recipes create-mdai
```

>_Note: Once the Engine installed your k8s context will be switched automatically to new cluster._

<div class="warning">
   <b>Other steps:</b>
   Upon installation you encounter an error where Docker is the culprit, please ensure the docker daemon is running. If this doesn't fix the error, feel free to:
   <ul>
      <li>
         Email us at <a href="mailto:support@mydecisive.ai">support@mydecisive.ai</a>
      </li>
      <li>
         File an issue under the <a href="https://github.com/DecisiveAI/mdai-inkops">MDAI InkOps Project</a>
      </li>
   </ul>
</div>

<br />

----

<span class="left"><a href="./semiautomated-install.md">⏪ Back to Semi-Automated Install</a></span>
<span class="right"><a href="./destroy.md">Next Step: Destroy ⏩</a></span>
