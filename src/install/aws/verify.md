# ✅⚖️ Trust But Verify ⚖️✅

## Verify the MDAI Engine via kubectl
Ensure your cluster is up and running.

### Verify namespaces

List out all namespaces

```shell
kubectl get ns
```

**Expected output**

[![Verify namespaces](/media/verify-get-ns.png)](/media/verify-get-ns.png)

### Verify pods

List out all pods in the default namespace.

```shell
kubectl get pods
```

**Expected output**

Your output for default configuration should be similar to:

[![Verify pods](/media/verify-get-pods.png)](/media/verify-get-pods.png)

## Verify the Console is up and running

### Step 1: Navigate to your AWS EC2 Load Balancer in the AWS Console

>*Note: Replace `AWS_REGION` with the region you deployed to.*

`https://AWS_REGION.console.aws.amazon.com/ec2/home?region=AWS_REGION#LoadBalancers`

### Step 2: Find the LB where the name is `mdai-console`

[![LB List](/media/lb-list.png)](/media/lb-list.png)

### Step 3: Copy DNS Name from `mdai-console` LB

[![LB DNS Name](/media/load-balancers.png)](/media/load-balancers.png)

### Step 4: Navigate to the URL and view the console

[![Console Data Flow](/media/console-data-flow.png)](/media/console-data-flow.png)

<br />

----

<p style="text-align: center;">
  <a href="./ingress.md">Back to Configure Ingress</a>
</p>
<p style="text-align: center;">
  <a href="./generate-telemetry.md">Next Step: Generate & Receive Telemetry >></a>
</p>
