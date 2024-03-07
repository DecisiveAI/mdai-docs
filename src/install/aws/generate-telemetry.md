## Generate and Collect telemetry

**What kind of user are you?**

1. I don't have any agents/collectors that I want to use at this time to send telemetry. **Use Option 1!**
2. I have sources of telemetry I'd love to send to my MDAI Engine™! **Use Option 2!**

### Option 1 - Use test data

1. Setup a Cronjob (or use on from the )
2. Apply to cluster
3. See telemetry coming through
4. Delete the job after you're done

_It is critical that you delete the cronjob, otherwise engine costs will increase as throughput and processing power are resource intense._

> Note: This is a great option if you're not ready to commit to the costs associated with ingress/egress. It's all local to the cluster you have just deployed, so there will not be additional charges, minus the compute required to generate and process the telemetry.

### Option 2 - Use real data

1. Find the source of data (collector/agent) you'd like to point at your MDAI Engine™ instance
2. Use your CNAME (from your host provider) or DNS (from AWS LB)
3. Configure your agent/collector to point to the CNAME or DNS
4. SEE RESULTS! Go to Validate step for more details.
