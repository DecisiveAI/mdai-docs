# Verify local MDAI Cluster
----

## Configure MDAI Console (UI) to use localhost

### Find your MDAI Console pod

One of the pods installed will contain a web app. Let's list out all cluster pods to find what your pod's name is.

_Note: the pod that starts with `mdai-console-<hash_id>`_

```shell
kubectl get pods
```

### Enable port forwarding from cluster to localhost

```shell
<!-- Example kubectl port-forward mdai-console-abcd123-xyz1 5173:5173 -->
kubectl port-forward <POD_NAME> <PORT>:<PORT>
```

### View Console on your desired port
You should now be able to view the MDAI Console at your newly configured port, in our case, we used `:5173`

🐙🎉 View yours at [http://localhost:<configured_port>](http://localhost:<configured_port>)

![A bright and shiny MDAI Cluster Console](../../media/console-new-and-shiny.png)


----
<span class="left"><a href="./install.md">⏪ Install</a></span>
<span class="right"><a href="../validate.md">Next Step: Validate ⏩</a></span>

