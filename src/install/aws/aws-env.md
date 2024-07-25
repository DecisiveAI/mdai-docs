# Let's update your AWS Environment Configs
----

Navigate to the `values/aws.env` file and start inputting the environment configuration that's relevant to your AWS account and infrastructure configurations.

## The AWS Basics

These fields are essential for AWS account access and resource control in AWS. These settings guarantee the MDAI Cluster will be installed in your desired account, region, and created with a user profile who has the correct permissions to create infrastructure. This is especially useful if these values differ from the default configurations in your AWS SSO/auth settings.

| Key          | Example Value    | Description |
| :----------  | :--------------- | :---------- |
| `AWS_REGION` | `us-east-1`      | AWS Region to be used for MDAI cluster creation  |
| `AWS_ACCOUNT`| `123123456`      | AWS Account to be used for MDAI cluster creation |
| `AWS_PROFILE`| `Admin-123123456`| AWS Profile to be used for MDAI cluster creation |

## MDAI Cluster - Helpful Contexts

| Key          | Example Value    | Description |
| :----------  | :--------------- | :---------- |
| `MDAI_CLUSTER_NAME` | `my-mdai-cluster` | A friendly name for your cluster  |

## READONLY: EC2 and EKS Configurations

***These values should be considered READONLY.***

The values can technically be changed, however this is the minimum required configuration for running the MDAI infrastructure with performance and cost in mind. You can adjust the values to fit your needs, note it's at your own risk. We have not tested beyond this configuration, but plan to in the near future.

| Key          | READONLY Value    | Description |
| :----------  | :--------------- | :---------- |
| `MDAI_EC2_INSTANCE_CLASS` | `t2`    | EC2 Class used for nodes in the EKS cluster |
| `MDAI_EC2_INSTANCE_SIZE`  | `micro` | EC2 Size used for nodes in the EKS cluster  |
| `MDAI_CLUSTER_CAPACITY`   | `12`    | Number of cluster EC2 nodes                 |


## Opt-in/out: MDAI Console UI Security

***This is an opt-in/out feature that enables security via authentication on the Console UI app. By default your MDAI Console application will be exposed to the open internet for anyone to access.*** 

Post-configuration, you will be presented with an option to configure more advanced authentication options in our [AWS Authentication for your MDAI Console](../aws/ui-auth/options.md) guide. 

If you choose to remain opt'd-out ignore fields `MDAI_UI_HOSTNAME` and `MDAI_UI_USER_POOL_DOMAIN`. 

| Key          | Example Value    | Description                                                                                                                                                                                                                                                                               |
| :----------  | :--------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COGNITO`                  | `false` (default)            | Opt-in to include Cognito in your cluster infrastructure                                                                                                                                                                                                                                  |
| `MDAI_UI_HOSTNAME`         | `mdai.yourdomain.dev`        | A required field to map your MDAI Console UI URL to your custom domain via a CNAME record. This hostname will also be used during the SSL Cert creation for this flow.                                                                                                                    |
| `MDAI_UI_USER_POOL_DOMAIN` | `yourdomain`                 | The domain name Cognito uses to bind your domain to, e.g., `yourdomain.com` would use `yourdomain` here. (https://yourdomain.auth.AWS_REGION.amazoncognito.com). This setting guarantees your domain will have a TLS (SSL) certificate auto-generated and auto-discovered during install. |


<div class="warning">
  Due to our MDAI Cluster's Load Balancer capabilities, alongside security measures, we're only able to support full MDAI Cluster compatibility with a <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-authenticate-users.html#cognito-requirements" target="_blank" rel="noreferrer noopener">limited list</a> of supported AWS Regions.<br />
  <b>Should you choose to opt-in to Cognito, please be sure the <code>AWS_REGION</code> you selected is part of the supported region.</b>
</div>


## Opt-in/out: Node AutoScaling

***Default should be true if you're unsure if you want this, please change to false.***

Karpenter provides dynamic and efficient scaling of your Kubernetes clusters. It automatically adjusts the number of nodes based on the current workload, ensuring optimal resource utilization and cost efficiency. 

| Key          | Example Value    | Description |
| :----------  | :--------------- | :---------- |
| `KARPENTER` | `true` (default)    | An opt-in/out feature that enables autoscaling on the EC2 node sizes you have selected. |

If you opt-in to this feature, we handle the configuration under the hood for you. You can read more about this configuration in our [Node AutoScaling Guide](../../advanced/autoscaling/node-autoscaling.md).

----
<span class="left"><a href="./repo.md">⏪ Back to: Check Us Out!</a></span>
<span class="right"><a href="./otel-config.md">Next Step: OTel config ⏩</a></span>
