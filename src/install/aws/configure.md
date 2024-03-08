<!-- toc -->

## Installing the MDAI Engine in AWS

The MDAI InkOps Toolkit will enable you to configure and deploy the MDAI Engine infrastructure in AWS.

🏁 Let's begin! 🏁

---

### Clone the MDAI InkOps Toolkit

Visit our GitHub repo to access our [MDAI InkOps Toolkit](https://github.com/DecisiveAI/mdai-inkops)

`git clone git@github.com:DecisiveAI/mdai-inkops.git`


Open the project from your local directory, based on your preferred workflow (IDE or terminal)

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
      <em>There are some pre-configured values. Please do not change these as we haven't tested configurations outside of these values and cannot guarantee functional engine behavior</em><br/><br/>
      The most important values to ensure correctness, are the `AWS_REGION` and `MDAI_UI_ACM_ARN`. <br/><br/>
      <code>AWS_REGION</code> - guarantees your engine gets installed in your preferred region if it differs from your default region as configured in your AWS SSO settings. <br/><br/>
      <code>MDAI_UI_ACM_ARN</code> - guarantees your domain has a SSL Certificate auto-generated, then auto-discoverd during install.<br/><br/>
    </p>
</div>

### Update the OTel configuration file

Ready to start collecting date via an OTel Collector? We have a some options...

#### Option 1 - Update Collector Configuration

We provided the default configuration for the Open Telemetry collector at `values/otelcol-config.yaml`.
Using our boilerplate will accelerate your deployment. If you have modifications you need to make, just follow the update commands in Option 2 below.

You can either use the config as it, which can be updated later, or you can start making modifications right now.
Find more information in the spec for the [OTEL Collector](https://opentelemetry.io/docs/collector/) to make the best decisions for your telemetry pipelines configuration.


#### Option 2 - BYO Config
Ready to commit to using your OTel configuration using the MDAI Engine? Simply update the configuration file (`values/otel-config.yaml`).


### Apply configuration to the MDAI Engine

After you've configured your engine, you can run the `config` command to automate the update to configuration files.

#### Step 1: Create an SSL certificate to apply to your custom domain
```shell
make cert
```

#### Step 2. Run the configuration script to take your values and apply them to the deployment configuration.
```shell
make config
```

---

🚀 It's time! Let's deploy 🚀
