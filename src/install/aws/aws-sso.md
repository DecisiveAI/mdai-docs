### Configuring AWS SSO

To deploy an MDAI Engine, you'll need to use the AWS CLI.

>**Note:** Our install steps use the recommended AWS CLI access method, AWS SSO. There are other [AWS CLI Access options](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html) that you can use to interact with your AWS account.

#### Login via the CLI

```shell
# Assumes your machine is already configured access to AWS via `aws configure sso`.
aws sso login --profile <AWS_PROFILE>
```

#### Choose the right AWS Account and AWS Role

<div class="warning">
  After configuration is complete, make sure you choose the correct AWS Role you want to use to deploy your engine. If you are unsure of which role to use, please contact your AWS system adminstrator.
</div>

![![Choose correct account](../../media/aws-account-selection.png)](../../media/aws-account-selection.png)

<br />

----

<p style="text-align: center;">
  <a href="./prerequisites.md">Back to Prerequisites</a>
</p>
<p style="text-align: center;">
  <a href="./repo.md">Next Step: Check us out! >></a>
</p>
