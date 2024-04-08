# Remove MDAI Engine
----
Tired of using the MDAI Engine locally? 😭 We're sorry to see you go, but we understand.

If you have feedback for us, please let us know why!
1. [Support team email](mailto:support@mydecisive.ai)
2. [Feedback form](https://docs.google.com/forms/d/e/1FAIpQLScZNGgu5Cshd-WP7HGcvW4yPVP_NbWswcAU6vKgUnRb_6umpA/viewform?usp=sharing)



### Automated uninstall
Follow the steps below to remove your local MDAI Engine

#### Ensure you have the correct k8s context selected.

Make sure your k8s context is set to `kind-mdai-local` cluster:

```bash
kubectl config get-contexts
```

Switch the context if needed:

```bash
kubectl cluster-info --context kind-mdai-local
```

#### Destroy Cluster

Run automated de-installation script

```bash
 make -f ./make/Makefile-local-recipes delete-mdai
```

#### Optional: Destroy all helm artifacts

If you want to remove all helm artifacts installed (you don't use it your other local setup), run the following

```bash
 make -f ./make/Makefile-local-recipes delete-mdai-all
```

----
<span class="left"><a href="./automated-install.md">⏪ Back to Automated Install</a></span>
<span class="right"><a href="./setup.md">Setup ⏩</a></span>
