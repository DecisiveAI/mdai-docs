# Using TelemetryGen to send data to MDAI Cluster

## Why use TelemetryGen?

Using [TelemetryGen](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/cmd/telemetrygen) is a great option if you're not ready to commit to the costs associated with ingress/egress to your cluster. It's all local to the cluster you have just deployed, so there will not be additional charges, minus the compute required to generate and process the telemetry.

## Let's begin!

In our example we'll 
1. Create or use an existing [cronjob](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/) or [job](https://kubernetes.io/docs/concepts/workloads/controllers/job/)
2. Apply the cronjob/job to your cluster
3. Watch telemetry flow through the console
4. Destroy the cronjob/job
5. Eat cake!

### Step 1 - Create or use cronjobs

You can create a [CronJob](https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/) (or use one from the `/jobs` directory).

### Step 2 - Apply the cronjob to your cluster

```shell
kubectl apply -f <cron_filename.yaml>
```

### Step 3 - Validate job is running

**Via kubectl**

```shell
# Get job by name - replace job-name with your cronjob's name
kubectl get cronjob job-name

# Still not enough? Watch your cronjob using the --watch command
kubectl get cronjob --watch
```

At this point, you should also be able to see data flowing through the MDAI Console to validate data flow. 

### Step 4 (optional, recommended) - Delete the cronjob once testing is complete

```shell
# Delete job by name - replace job-name with your cronjob's name
kubectl delete cronjob job-name
```

<div class="warning">
  <em>It is critical that you delete the cronjob once testing is complete, otherwise MDAI Cluster costs will continue to increase as the MDAI Cluster continues to processes all incoming telemetry data.</em>
</div>

#### Step 5 - Eat cake 🍰! 

You sent your first telemetry record to MDAI!

🎉 That's it! Your MDAI Cluster is now ready to use! 🎉


## Want more ways to send your cluster data?

Still curious about the other ways to generate and send telemetry? 

* [Send sample data with Postman](./postman.md.md)
* [Send sample data via terminal](./curl_grpcurl.md)
* [Setup your collectors with live agents/collectors](./real_collector_agent.md.md)

<br />

----
<span class="right"><a href="../installation.md">⏪ Back to Intro: Generate and Receive Telemetry</a></span>