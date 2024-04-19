# Let's update your AWS Environment Configs
----

Navigate to the `values/aws.env` file and start inputting the environment configuration that's relevant to your AWS account.

<div class="warning">
  Due to our engine's Load Balancer capabilities alongside security measures, we're only able to support full engine compatibility with a <a href="https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-authenticate-users.html#cognito-requirements" target="_blank" rel="noreferrer noopener">limited list</a> of AWS Regions.
</div>

```
# region where the engine going to be installed.
AWS_REGION=

# AWS account to be used
AWS_ACCOUNT=

# AWS profile to be used
AWS_PROFILE=

# Class and size of the EC2 used for EKS k8s cluster
# this is the minimum required configuration, adjust to your needs
MDAI_EC2_INSTANCE_CLASS=t2
MDAI_EC2_INSTANCE_SIZE=micro

# Number of cluster EC2 nodes
MDAI_CLUSTER_CAPACITY=10

# Amazon Resource Name (ARN) of the certificate to be used for the Console endpoint
MDAI_UI_HOSTNAME=

# The domain name to tie your auth to, e.g., 'example.com' would use 'example' here
MDAI_UI_USER_POOL_DOMAIN=
```

<div class="warning">
  <p>
    <b>Note</b>
    <p>
      <em>The above code includes some pre-configured values. Please do not change these as we have not yet tested configurations outside of these values and cannot guarantee functional engine behavior.</em><br/><br/>
      The most important values for you to enter are `AWS_REGION`, `MDAI_UI_ACM_ARN` and `MDAI_UI_USER_POOL_DOMAIN`. <br/><br/>
      <code>AWS_REGION</code> - This setting guarantees the engine will be installed in your desired region, if that region differs from the default region configured in your AWS SSO settings. <br/><br/>
      <code>MDAI_UI_ACM_ARN</code> - This setting guarantees your domain will have a TLS (SSL) certificate auto-generated and auto-discovered during install.<br/><br/>
      <code>MDAI_UI_USER_POOL_DOMAIN</code> - This setting will create some auto configs/mappings to help put auth into your public facing urls -- namely the MDAI Console <br/><br/>
    </p>
</div>


----
<span class="left"><a href="./repo.md">⏪ Back to: Check Us Out!</a></span>
<span class="right"><a href="./otel-config.md">Next Step: OTel config ⏩</a></span>
