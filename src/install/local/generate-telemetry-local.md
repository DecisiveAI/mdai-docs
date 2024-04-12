# Generate and Receive Telemetry - Local
----

## What kind of user are you?

1. I don't have any existing agents/collectors that I can use to send telemetry right now. **Use Option 1!**
2. I have existing sources of telemetry I'd love to point to my new engine! **Use Option 2!**

### Option 1 - Use test data

Using [TelemetryGen](https://example.com) is a great option if you're not ready to commit to the costs associated with ingress/egress. It's all local to the cluster you have just deployed, so there will not be additional charges, minus the compute required to generate and process the telemetry.


#### Step 1 - Create or use cronjobs
You can create a [CronJob](https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/) (or use one from the `/jobs` directory).

#### Step 2 - Apply the cronjob to your cluster
```shell
kubectl apply -f <cron_filename.yaml>
```

#### Step 3 - Validate job is running

**Via kubectl**

```shell
# Get job by name - replace job-name with your cronjob's name
kubectl get cronjob job-name

# Still not enough? Watch your cronjob using the --watch command
kubectl get cronjob --watch
```

#### How to delete the cronjob once testing is complete

```shell
# Delete job by name - replace job-name with your cronjob's name
kubectl delete cronjob job-name
```
<div class="warning">
  <em>It is critical that you delete the cronjob once testing is complete, otherwise engine costs will continue to increase as the engine continues to processes all incoming telemetry data.</em>
</div>

### Option 2 - Use real data

>Visit the [OTel Collector Docs site](https://opentelemetry.io/docs/collector/configuration/) to learn more about configuring your collector based on your specific data sources and destinations.

A general workflow is as follows:

1. Determine which sources of data (collector/agent) you'd like to point at your MDAI Engine instance.
2. Use your CNAME (from your host provider) or DNS (from AWS LB) as mentioned in our [Ingress documentation](./ingress.md).
3. Configure your agent/collector to point to the CNAME or DNS as mentioned in our [Ingress documentation](./ingress.md).
4. SEE RESULTS! [Verify data flow](./verify.md)

🎉 That's it! Your MDAI Engine is now ready to use! 🎉

<br />

----
<span class="left"><a href="./verify.md">⏪ Back to Verify Installation</a></span>
<span class="right"><a href="./validate.md">Next Step: Validate ⏩</a></span>
