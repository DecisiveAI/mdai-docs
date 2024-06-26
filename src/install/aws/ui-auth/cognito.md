# 🔒 Cognito
----

We knew it wouldn't be acceptable to leave your precious new resources unprotected and open to any user of the internet!

*...Enter Cognito...*

We've added the ability to connect [Amazon Cognito](https://aws.amazon.com/cognito/) easily to your new MDAI Cluster to limit access for undesired users.

<div class="warning">
  Cognito is not supported in all AWS Regions. If you run into issues
  post-install, this is likely the reason. A typical error you would see looks like this:<br />
  <code style="color: #d10707;">
    Failed deploy model due to failed to create listener rule: ValidationError: Action type 'authenticate-cognito' must be one of 'redirect,fixed-response,forward,authenticate-oidc' status code: 400, request id: ########-####-####-####-############
  </code><br /><br />
  <b>The above error can be found in the AWS Console > EKS service.</b><br /><br />
  You can access the ingress output manually:<br />
  <code>
    EKS > Clusters > [YOUR_CLUSTER] > Resources > Service and networking > Ingresses > ui-alb-ingress
  </code><br /><br />
  You can access the ingress output by hitting this link after updating the values in brackets:<br />
  <code>
    https://[AWS_REGION].console.aws.amazon.com/eks/home?region=[AWS_REGION]#/clusters/[YOUR_CLUSTER]/ingresses/ui-alb-ingress?namespace=default
  </code><br />
</div>

Our installation includes the following resources upon creating an MDAI Cluster:

1. [User pool](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html) `mdai-user-pool`
2. [App client](https://docs.aws.amazon.com/cognito/latest/developerguide/user-pool-settings-client-apps.html) `mdai-app-client`

## ⚙️ Pre-built configuration

The following environment variables need to be defined in `values/aws.env` during the pre-build configuration step:

`MDAI_UI_HOSTNAME`
This is a hostname for the UI endpoint, which is going to be used as a main UI hostname. This should directly relate to a DNS CNAME record, pointing to DNS hostname, generated by AWS for the Load Blancer `mdai-console` endpoint.

`MDAI_UI_USER_POOL_DOMAIN`
This variable contains a prefix for [User pool domain](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-assign-domain.html).
[Amazon Cognito domain](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-assign-domain-prefix.html)
is used with this installation, so this variable represents a prefix, for the domain.
This domain name will become a part of the auth redirecting URL.

## 🧍User(s) creation

The only manual step required is a user(s) creation.

### Option 1: Via the AWS Console UI
Please follow the [Amazon Cognito User Pool documentation](https://docs.aws.amazon.com/cognito/latest/developerguide/managing-users.html) steps
to create users(s) in `mdai-user-pool`.

### Option 1: Via the AWS CLI

If you prefer to use the command line, this quick command will find the user group created as a result of the MDAI stack and perform the user create operations. 

```shell
for up_id in $(aws cognito-idp list-user-pools --max-results 1  --region <your-region> --profile <your-profile> --query 'UserPools[?Name==`mdai-user-pool`].[Id]' --output text); do
    echo "Creaded user ${up_id}"
    aws cognito-idp admin-create-user --user-pool-id $up_id --username user@yourdomain.com --temporary-password P@55w0rd_fun --region <your-region> --profile <your-profile>
done

```


----
<span class="left"><a href="../validate.md">⏪ Back to: Validate Installation</a></span>
<span class="right"><a href="../lifecycle/overview.md">Next Step: Lifecycle Overview ⏩</a></span>