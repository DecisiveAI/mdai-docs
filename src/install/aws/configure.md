<!-- toc -->

## Configuring Your MDAI Engine in AWS

The MDAI InkOps Toolkit will enable you to configure and deploy your MDAI Engine infrastructure in AWS.

🏁 Let's begin! 🏁

---

### Clone the MDAI InkOps Toolkit

Visit our GitHub repo to access our [MDAI InkOps Toolkit](https://github.com/DecisiveAI/mdai-inkops)

`git clone git@github.com:DecisiveAI/mdai-inkops.git`


Open the project from your local directory, based on your preferred workflow (IDE or terminal).

```
cd mdai-inkops

code mdai-inkops
```

### Update the environment configuration file

Navigate to the `values/aws.env` file and start inputting the environment configuration that's relevant to your AWS account.

```
# region where the engine going to be installed
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

# Amazon Resource Name (ARN) of the certificate to be used for the Engine UI endpoint
MDAI_UI_HOSTNAME=
```

<div class="warning">
  <p>
    <b>Note</b>
    <p>
      <em>The above code includes some pre-configured values. Please do not change these as we have not yet tested configurations outside of these values and cannot guarantee functional engine behavior.</em><br/><br/>
      The most important values for you to enter are `AWS_REGION` and `MDAI_UI_ACM_ARN`. <br/><br/>
      <code>AWS_REGION</code> - This setting guarantees the engine will be installed in your desired region, if that region differs from the default region configured in your AWS SSO settings. <br/><br/>
      <code>MDAI_UI_ACM_ARN</code> - This setting guarantees your domain will have a TLS (SSL) certificate auto-generated and auto-discovered during install.<br/><br/>
    </p>
</div>

### Update the OTel configuration file

Ready to start collecting some data via an OTel Collector? You've got a couple options...

#### Option 1 - Update Collector Configuration

We have provided a default configuration for the Open Telemetry collector at `values/otelcol-config.yaml`.
Using our boilerplate will accelerate your deployment, but if you need to make modifications, please follow the update commands in Option 2 below.

You can either use the config as is, then update it later, or you can start making modifications right now.
Learn more about the specifications for the [OTEL Collector](https://opentelemetry.io/docs/collector/) to make the best decisions for your telemetry pipelines configuration.


#### Option 2 - Bring Your Own Configuration
Want to use a custom OTel configuration file? Simply update the configuration file here: (`values/otel-config.yaml`).


### Apply configuration to the MDAI Engine

After you've configured your engine, you can run the `config` command to automate the update to your configuration files.

#### Step 1: Create a TLS (SSL) certificate for your custom domain
```shell
make cert
```

#### Step 2. Run the configuration script to take your values and apply them to the deployment configuration
```shell
make config
```

<br />

----

🚀 It's time! Let's deploy 🚀

<p style="text-align: center;">
  <a href="./aws-sso.md">Back to Configure AWS SSO</a>
</p>
<p style="text-align: center;">
  <a href="./deploy.md">Next Step: Deploy Your MDAI Engine! >></a>
</p>
