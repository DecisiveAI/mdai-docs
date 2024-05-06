# Uninstall the MDAI Nucleus

----

Tired of using the MDAI Nucleus? 😭 We're sorry to see you go, but we understand.

## Feedback - Where are the rough edges?

We'd love to hear your thoughts! Please let us know how we can improve by:

* Filling our [Feedback form](https://docs.google.com/forms/d/e/1FAIpQLScZNGgu5Cshd-WP7HGcvW4yPVP_NbWswcAU6vKgUnRb_6umpA/viewform?usp=sharing)
* Emailing us Feedback to our [Support Team](mailto:support@mydecisive.ai)

## 🧨 Time to destroy

Due to AWS CDK limitations several additional steps required to fully remove all MDAI Nucleus resources from AWS. Follow the steps below, in order, to destroy your Nucleus and all associated resources.


### Remove all OTel collector instances within your Nucleus
```shell
kubectl describe otelcol $(kubectl get otelcol -o custom-columns=":.metadata.name")
```

### Remove the helm chart for the console
```shell
helm uninstall mdai-console
```

### Delete the Open Telemetry Collector
```shell
kubectl delete otelcol/<your_collector_name>
```

### Destroy MDAI Nucleus stack
```shell
# List stacks to ensure you choose the correct stack to be deleted
aws cloudformation list-stack-sets --profile <your_aws_profile> --region <your_aws_region>
```

```shell
# Delete the stack set
aws cloudformation delete-stack-set --stack-set-name <your-stack-set> --profile <your_aws_profile> --region <your_aws_region>
```

**Note**: The destroy process will run for a while and may, and likely will, return an error due some resources having dependencies and being deleted out of order. You can find work arounds


### Troubleshooting Destroy - Manual Steps

Delete listed dependencies by following steps below or through AWS Console.

#### Get your UI Load Balancer ARN

The following command will return an AWS ARN if your UI Load Balancer has not been deleted. Save this ARN for the next step.

```shell
aws elbv2 describe-load-balancers \
--region <your_region>  \
--profile <your_profile> \
--query "LoadBalancers[?contains(LoadBalancerName,'mdai-console')].{ARN:LoadBalancerArn}" \
--output text
```

#### Delete your UI Load Balancer
Use the ARN returned from the previous command (👆) to delete pending load balancer...

```shell
aws elbv2 delete-load-balancer \
--load-balancer-arn <your_load_balancer_arn> \
--region <your_region> \
--profile <your_profile>
```

#### Delete Security Groups

If the destroy failed to delete the VPC, you'll need to delete the Security Groups related to the VPC. Use the VPC ID from the cdk error output:

```shell
for sg_id in $(aws ec2 describe-security-groups --region <your_region> --profile <your_profile> --filters Name=vpc-id,Values='<your_vpc_id>' --query 'SecurityGroups[?GroupName!=`default`].[GroupId]' --output text); do
    aws ec2 delete-security-group --group-id $sg_id --region <your_region> --profile <your_profile>
    echo "Deleted security group $sg_id"
done
```

#### Run the destroy process again

At this point, you should be able to run the destroy stack at [STEP: ](./uninstall.md)
