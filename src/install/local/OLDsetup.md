# Setup Environment
----
## Create a cluster where the Engine can be installed. For our example, we'll use kind.
   > ```@shell
   > <!--  Create cluster -->
   > kind create cluster --name mdai-local
   >
   > <!-- Check that your cluster is up and running -->
   > kind get clusters
   > ```
## Setup and configure a local instance of the MDAI Engine

   > ```shell
   > make local-deploy
   > kubectl-config
   > ```

## Ensure your cluster is up and running.

   > ```@shell
   > kubectl get pods
   > ```
   >
   > _Note: the pod that starts with `mydecisive-engine-ui-_`\*

## Enable port forwarding from cluster to localhost

   > ```
   > <!-- Example kubectl port-forward mydecisive-engine-ui-578f644b7-k9q47 5173:5173 -->
   >
   > kubectl port-forward <POD_NAME> <PORT>:<PORT>
   > ```


----

## View the MDAI Console at [http://localhost:5173](http://localhost:5173) 🐙🎉

![A bright and shiny MDAI Engine Console](../../media/console-new-and-shiny.png)



----
<span class="left"><a href="./uninstall.md">⏪ Back to Uninstall</a></span>
<span class="right"><a href="./generate-collect.md">Next Step: Generate Telemetry ⏩</a></span>

