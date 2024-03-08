## Deploying to AWS

**💪 You're ready to deploy your MDAI Engine instance! 💪**

Ready to see the Engine in action?
<div class="warning">
  Note: After deploying, the engine will be active and running in AWS. There are costs associated with running our engine, however, we've done all we can to make the infrastructure as cost-effective as possible
</div>

### Deploy the MDAI Engine

```shell
make install
```
<div class="warning">
  <b><em>Don't walk away just yet!</em></b>
  <p>There's one more manual verification step/check before CloudFormation will deploy the stack</p>
</div>


### The install workflow
1. Install will check and bootstrap the CDK Toolkit if it's not present for the region.
![[bootstrap.png](../media/bootstrap.png)](/media/bootstrap.png)

2. CDK will output the detected changes and ask to accept or reject the changes. Review carefully before proceeding.
![![stack-details.png](/media/stack-details.png)](/media/stack-details.png)

3. Follow the progress of the stack creation through the terminal
[![stack-details.png](/media/stack-details.png)](/media/stack-details.png)
*or AWS Console -> Cloud Formation*
[![CFN Status](/media/cfn-status.png)](/media/cfn-status.png)
4.  The installation process will add a new context to your `kubeconfig`. You can switch context by running `kubectl config use-context <desired_context>`
Detailed output stored into `cdk-output.json`.

### A few notes while your stack is building...

1. 🍿 Grab some popcorn! Average install time is between 20-30 minutes.

2. 👀 Don't want to monitor your terminal? Check out the your stack's status in the AWS Console.
```
<!-- Change AWS_REGION to the region you deployed to -->
https://AWS_REGION.console.aws.amazon.com/cloudformation/home?region=AWS_REGION#/stacks?filteringText=&filteringStatus=active&viewNested=true
```

3. 🏛️ View your stack's architecture in the CloudFormation Designer tool for your stack
Find stack ARN

[![CFN Stack ARN](/media/cfn-stack-arn.png)](/media/cfn-stack-arn.png)

```
<!-- Change AWS_REGION to the region you deployed to -->
<!-- Change STACK_ARN to your stack's ARN -- shown above  -->
https://AWS_REGION.console.aws.amazon.com/cloudformation/designer/home?region=AWS_REGION&stackId=<STACK_ARN>#
```

1. 🛠️ Build a local version while you're waiting! [QuickStart](../local/quick-start.md)
