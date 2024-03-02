## Destroy the MDAI Engine™

Due to AWS CDK limitations several additional steps required to fully remove all MDAI Engine™ resources from AWS.

1. Delete the Open Telemetry Collector
```shell
kubectl delete otelcol/<your_collector_name>
```
1. Destroy MDAI Engine™ stack
```shell
cdk destroy --profile <your_aws_profile>
```
The destroy process will run for a while and may return an error due some resources having dependencies.
Delete listed dependencies by following steps below or through AWS Console.

Run the command bellow to check if UI load balancer has to be deleted:
```shell
aws elbv2 describe-load-balancers --region <your_region> --profile <your_profile> --query "LoadBalancers[?contains(LoadBalancerName,'mydecisive-engine-ui')].{ARN:LoadBalancerArn}" --output text
```
Use the ARN from the command above to delete pending load balancer:
```shell
aws elbv2 delete-load-balancer --load-balancer-arn <your_load_balancer_arn> --region <your_region> --profile <your_profile>
```
Delete security groups if the destroy failed to delete the VPC. Use the VPC ID from the cdk error output:
```shell
for sg_id in $(aws ec2 describe-security-groups --region <your_region> --filters Name=vpc-id,Values='<your_vpc_id>' --query 'SecurityGroups[?GroupName!=`default`].[GroupId]' --output text); do
    aws ec2 delete-security-group --group-id $sg_id --region <your_region>
    echo "Deleted security group $sg_id"
```
and run the destroy process again.
