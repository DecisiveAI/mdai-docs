# Generate and Receive Telemetry - Local
----

## What kind of user are you?

1. I don't have any existing agents/collectors that I can use to send telemetry right now. **Use Option 1!**
2. I have existing sources of telemetry I'd love to point to my new MDAI Cluster! **Use Option 2!**

### Option 1 - Use test data

Using [TelemetryGen](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/cmd/telemetrygen) is a great option if you're not ready to commit to the costs associated with ingress/egress. It's all local to the cluster you have just deployed, so there will not be additional charges, minus the compute required to generate and process the telemetry.


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
  <em>It is critical that you delete the cronjob once testing is complete, otherwise MDAI Cluster costs will continue to increase as the MDAI Cluster continues to processes all incoming telemetry data.</em>
</div>


### Option 2 - Use real data

>Visit the [OTel Collector Docs site](https://opentelemetry.io/docs/collector/configuration/) to learn more about configuring your collector based on your specific data sources and destinations.

A general workflow is as follows:

1. Determine which sources of data (collector/agent) you'd like to point at your MDAI Cluster instance.
2. Use your CNAME (from your host provider) or DNS (from AWS LB) as mentioned in our [Ingress documentation](../advanced/ingress.md).
3. Configure your agent/collector to point to the CNAME or DNS as mentioned in our [Ingress documentation](../advanced/ingress.md).
4. SEE RESULTS! [Verify data flow](./verify.md)

#### 

Note the External-IP for the test-collector-collector from the following command. You will need this to send telemetry from your agents/collectors of choice.

```bash
kubectl get svc test-collector-collector -n default
```


### Option 3 - Use our Postman collection

Use our [postman collection](https://github.com/DecisiveAI/postman)


### Option 4 - Use `curl` and `grpcurl`

See [our request docs](https://github.com/DecisiveAI/mdai-inkops/tree/task/july-15-updates/examples) for more information




🎉 That's it! Your MDAI Cluster is now ready to use! 🎉

<br />

----

## Coming from Local Install?

<span class="left" style="width: 50%">
  <a href="./local/verify.md">⏪ Back to Verify Installation</a>
</span>
<span class="right" style="width: 50%">
  <span>Want to validate telemetry data flowing through your pipelines?</span>
  <br />
  <a href="./local/validate.md">Next Step: Validate ⏩</a>
  <br />
  <br />
  <span>Know how to validate data flow already?</span>
  <a href="congrats.md">Next Step: Congrats! ⏩</a>
</span>

<br />
<br />
<br />
<br />
<br />

## Coming from AWS Install?

<div>
  <span class="left" style="width: 50%">
    <a href="./aws/verify.md">⏪ Back to Verify Installation</a>
  </span>
  <span class="right" style="width: 50%">
    <span>Want to validate telemetry data flowing through your pipelines?</span>
    <br />
    <a href="./aws/validate.md">Next Step: Validate ⏩</a>
    <br />
    <br />
    <span>Know how to validate data flow already?</span>
    <a href="congrats.md">Next Step: Congrats! ⏩</a>
  </span>
</div>
