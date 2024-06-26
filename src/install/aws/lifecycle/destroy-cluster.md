# Destroy MDAI Cluster

----

Tired of using the MDAI Cluster? 😭 We're sorry to see you go, but we understand. If you have feedback for us, please fill out.

When decommissioning a cluster or performing a clean-up operation, you need to delete all resources and configurations.

## How to Destroy


Follow the steps below to destroy the AWS Stack.
Due to AWS CDK limitations several additional steps required to fully remove all MDAI Cluster resources from AWS.

- Delete the Open Telemetry Collector
  ```shell
  kubectl delete otelcol/<your_collector_name>
  ```
- Destroy MDAI Cluster stack
  ```shell
  cdk destroy --profile <your_aws_profile>
  ```
- The destroy process will run for a while and may return an error due some resources having dependencies.
Delete listed dependencies by following steps below or through AWS Console.

    - Run the command bellow to check if UI load balancer has to be deleted:
        ```shell
        aws elbv2 describe-load-balancers \
        --region <your_region>  \
        --profile <your_profile> \
        --query "LoadBalancers[?contains(LoadBalancerName,'mdai-console')].{ARN:LoadBalancerArn}" \
        --output text
        ```
    - Use the ARN from the command above to delete pending load balancer:
        ```shell
        aws elbv2 delete-load-balancer \
        --load-balancer-arn <your_load_balancer_arn> \
        --region <your_region> \
        --profile <your_profile>
        ```
    - Delete security groups if the destroy failed to delete the VPC. Use the VPC ID from the cdk error output:
        ```shell
        for sg_id in $(aws ec2 describe-security-groups --region <your_region> --profile <your_profile> --filters Name=vpc-id,Values='<your_vpc_id>' --query 'SecurityGroups[?GroupName!=`default`].[GroupId]' --output text); do
            aws ec2 delete-security-group --group-id $sg_id --region <your_region> --profile <your_profile>
            echo "Deleted security group $sg_id"
        done
        ```
- Run the destroy process again.


1. Delete all artifacts associated with the cluster using `kubectl delete -f cluster-manifests/`.
2. Confirm the deletion of pods, services, deployments, and other resources, effectively destroying the Kubernetes cluster.


### Data Persistence - Prometheus

<div class="warning">
  <p>
    Currently, there is no data persistence for Prometheus. If you destroy your MDAI Cluster, you'll also be destroying your prometheus instance and all associated data. 🪦
  </p>
  <p>
    Until MDAI is able to support a more robust persistence layer or snapshot capability, we recommend using a <a href="https://prometheus.io/docs/prometheus/latest/storage/#remote-storage-integrations" target="_blank">remote storage option</a> for your persistence needs.
  </p>
</div>

<br />

----
<span class="left"><a href="./disable-MDAI Cluster.md">⏪ Back to: Disable MDAI Cluster </a></span>
<span class="right"><a href="../../congrats.md">Next Step: Congrats  ⏩</a></span>