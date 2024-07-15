# Uninstall the MDAI Cluster

----

Tired of using the MDAI Cluster? 😭 We're sorry to see you go, but we understand.

## Feedback - Where are the rough edges?

We'd love to hear your thoughts! Please let us know how we can improve by:

* Filling our [Feedback form](https://docs.google.com/forms/d/e/1FAIpQLScZNGgu5Cshd-WP7HGcvW4yPVP_NbWswcAU6vKgUnRb_6umpA/viewform?usp=sharing)
* Emailing us Feedback to our [Support Team](mailto:support@mydecisive.ai)

## 🧨 Time to destroy

Due to AWS CDK limitations several additional steps required to fully remove all MDAI Cluster resources from AWS. Follow the steps below, in order, to destroy your MDAI Cluster and all associated resources.


### Remove the helm chart for the console
```shell
helm uninstall mdai-console
```


### Scripts for destroying MDAI Cluster stack

#### Step 1: Allow scripts to be executed

You may need to give access to the destroy scripts if you don't have permissions to execute them

```shell
chmod +x ./make/scripts/delete-load-balancers.sh
chmod +x ./make/scripts/delete-stack.sh
chmod +x ./make/scripts/delete-network-artifacts.sh
```

#### Step 2: Ensure you have your env variable available

Upon MDAI Cluster creation you should have a `.env` file full of variables. It will look something like the example below, but with values populated. 

```
MDAI_UI_ACM_ARN=
AWS_REGION=
AWS_ACCOUNT=
AWS_PROFILE=
MDAI_EC2_INSTANCE_CLASS=
MDAI_EC2_INSTANCE_SIZE=
MDAI_CLUSTER_CAPACITY=
MDAI_CLUSTER_NAME=
COGNITO=
MDAI_UI_HOSTNAME=
MDAI_UI_USER_POOL_DOMAIN=
AWS_SSO_ROLE=
```

<div class="warning">
  Our scripts will use these environment variables to run their scripts so be sure to double check you're running the scripts on the correct environment.  
</div>

#### Step 3: Delete all your load balancers

This step is instantaneous and you shouldn't have to wait at all for changes to take effect.

```shell
./make/scripts/delete-load-balancers.sh
```

#### Step 4: Delete your stack

Grab your popcorn! 🍿 This step takes anywhere from 15-20 minutes as you'll be deleting all the artifacts related to the cluster from installation.

<div class="warning">
  <b>Note</b>: The destroy process will run for a while and may, and likely will, return an error due some resources having dependencies and being deleted out of order. Once the delete fails, please proceed to steps 5 & 6.
</div>


```shell
# Delete the stack
./make/scripts/delete-stack.sh
```

You should be able to following the delete progress in one of two ways...
1. Via the AWS Console UI (replace `AWS_REGION` with your desired region)
```
https://AWS_REGION.console.aws.amazon.com/cloudformation/home?region=AWS_REGION#/stacks?filteringText=&filteringStatus=active&viewNested=true
```
2. Via the CLI
```shell
aws cloudformation describe-stacks \
    --stack-name "$STACK_NAME" \
    --region "$REGION" \
    --profile "$PROFILE" \
    --query "Stacks[0].StackStatus" \
    --output text
```

<p>
  🎵 Here's some <a href="https://youtu.be/Eo-KmOd3i7s?feature=shared&t=11" target="_blank">mood music</a> while you wait. 🎵
</p>


#### Step 5: Delete network artifacts

One of the main reasons your stack fails in the networking layer of your cluster. This script should help delete the artifacts and resources related to networking.

```shell
./make/scripts/delete-network-artifacs.sh
```

<div class="warning">
  <b>Note</b>: You may need to run this a couple times to succeed, however, if you continue to see artifacts not deleting via messaging, you can use step 6 to finalize the destroy process. 
</div>


#### Step 6: Force delete the stack 

```shell
./make/scripts/force-delete-stacks.sh
```

#### Step 7: Run the destroy process again via AWS Console UI

If all else fails, you should be able to visit your Stack url in the AWS Console UI and `retry delete` with the *force delete* option.

----
<span class="left"><a href="./enable-MDAI Cluster.md">⏪ Back to: Enable MDAI Cluster ⏩</a></span>
<span class="right"><a href="../../testing.md">Next Step: Generate Telemetry ⏩</a></span>