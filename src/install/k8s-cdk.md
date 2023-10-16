# Deploy a new EKS cluster with AWS CDK

You may use [the MyDecisive Engine AWS CDK app](#) to provision a new AWS EKS cluster running the MyDecisive Engine.

<div class="warning">
Deploying an AWS EKS cluster will result in AWS costs, for the cluster and its underlying resources.
</div>

## Prerequisites

- Access to an AWS account and admin privileges to that account
- [Node.js](#) and the [AWS SDK](#) installed on the machine you wish to deploy from

## Steps

1. Clone the [CDK application repo](#) to your installing machine
2. Run the following to prepare the CDK app for deployment:

```shell
npm i
```

3. Run this command to have CDK synthesize the EKS stack and see a preview of the resources to be deployed, replacing the relevant values:

```shell
cdk diff --region=AWS_REGION --profile=AWS_CLI_PROFILE_NAME --account=ACCOUNT_NUMBER
```

4. Run this command to deploy the EKS cluster with the MyDecisive Engine:

```shell
cdk deploy DecisiveEngine --region=AWS_REGION --profile=AWS_CLI_PROFILE_NAME
```

## Uninstallation

To remove the engine and the deployed EKS cluster, run the following:

```shell
cdk destroy DecisiveEngine --region=AWS_REGION --profile=AWS_CLI_PROFILE_NAME
```

<div class="warning">
The CDK uninstall process may appear to fail, citing some resources that could not be destroyed, such as EC2 subnets/VPCs. You may have to go to the AWS CloudFormation console to find these resources and delete them manually. This is a limitation of CloudFormation and CDK.

Once you have deleted these stuck resources, also delete the CloudFormation stack from the CloudFormation console to clean the remaining artifacts from your AWS environment.

</div>
