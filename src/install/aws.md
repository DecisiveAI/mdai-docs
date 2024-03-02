# Cloud Install - AWS

<!-- toc -->

## Setup the MDAI Engine™ in AWS

You are going to learn to do the following in less than five minutes:

- Set up and run a cloud instance of MDAI Engine™
- Send telemetry to the MDAI Engine™
- Access the MDAI Engine Console™ to verify data flowing through the MDAI Engine™.

## Prerequisites

### System Requirements

Make sure that your developer environment has the following. This page assumes that you’re using bash. Adapt configuration and commands as necessary for your preferred shell.

- Install [Go](https://go.dev/dl/) (1.20 or higher) from source or use homebrew `brew install go`
- [GOBIN environment variable](https://pkg.go.dev/cmd/go#hdr-Environment_variables) is set; if unset, initialize it appropriately, for example:

```
export GOBIN=${GOBIN:-$(go env GOPATH)/bin}
```

- Install [npm](https://nodejs.org/en/download) from source or use homebrew `brew install npm`
- Install [aws-cdk](https://docs.aws.amazon.com/cdk/v2/guide/cli.html) from source or use homebrew `brew install aws-cdk`. AWS CDK (requires Node.js ≥ 14.15.0)
<!-- * Install [docker](https://www.docker.com/get-started/)-->

### AWS SSO

- Install [AWS SSO](https://docs.aws.amazon.com/cli/latest/userguide/sso-configure-profile-token.html)
- Login via the CLI

```@bash
aws configure sso
```

- After configuration is complete, make sure you choose the correct AWS account you want to deploy your engine to.
  ![Choose correct account](../media/aws-account-selection.png)

### AWS CDK

Follow the steps in the [AWS CDK Install Guide](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_install). Don't forget to [Bootstrap](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html#getting_started_bootstrap) your environment!

```@bash
# Install CDK
npm install -g aws-cdk

# Get your AWS account
aws sts get-caller-identity --profile <your_aws_profile>

# Check if you have already Bootstrap'ed your environment
aws cloudformation describe-stacks \
		--stack-name CDKToolkit \
		--region ${AWS_REGION} || \
		CDK_NEW_BOOTSTRAP=1 $(CDK) bootstrap

# Bootstrap your environment
cdk bootstrap aws://<your_aws_account>/us-east-1 --profile <your_aws_profile>
```

## Installing the MDAI™ Engine in AWS

### Update the environment configuration file

TODO: update this info it's shit
Update the vaules/aws.

### Update the Otel configuration file

TODO: Add context
Option 1: don't change
Option 2: BYO

### Configure the MDAI™ Engine

```@bash
# Configure engine

make config
```

_Optional: Check .env file to update region, if needed_

### Deploy the MDAI™ Engine

```@bash
make install
```

_Note: Detailed output stored into cdk-output.json_

Ensure your cluster is up and running.

```@bash
kubectl get pods
```

_Note: the pod that starts with `mydecisive-engine-ui-_`\*

### Enable access to Engine via DNS Mappings to Load Balancer Endpoints

There are three entry points to the engine:

1. **gRPC Load Balancer Endpoint** - enables gRPC telemetry to be sent to the engine.
2. **http Load Balancer Endpoint** - enables http telemetry to be sent to the engine
3. **console-ui Load Balancer Endpoint** - serves the MDAI Console for monitoring your engine instance

In order to enable access allowed external access to the engine, you need to do the following:

**Identify the Load Balancer DNS names**

1. In the AWS Console, navigate to your [EC2 Load Balancers endpoints](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#LoadBalancers) _Note: link above take you to region: us-east-1, you will need to change if you've deployed your engine in a different region_
2. Locate the three load balancers required to run an MDAI Engine™, there should be a gRPC, http, and console-ui load balancer. Make note of each of the load balancer's DNS names. ![load balancers](../media/load-balancers.png)

**Generate Certificates for secure connections to your MDAI Engine™ Instance**
Follow the instructions in the [AWS ACM Certificate Request Guide](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html#request-public-console) to verify your domain and acquire a certificate for secure connections to your MDAI Engine™ instance.

**Certificate Strategy**
_Option 1: Default setup_

1. **gRPC certificate** - enables a secure connection to the gRPC endpoint of your engine instance
2. **non-gRPC cert** - enables a secure connection to the non-gRPC endpoint of your engine instance
3. **console-ui certificate** - enables a secure connection to the engine console within your engine instance

_Option 2: Wildcard setup_

This will allow you to use a single certificate for all your endpoints.

> Note: AWS doesn't provide free wildcard certificates.

**Update the DNS Mapping**

1. Log into your Domain Administrator Tool
2. Update DNS mapping ([GoDaddy Example](https://www.godaddy.com/help/add-a-cname-record-19236)) to add a CNAME Record for each relevant Load Balancers created by engine.

**DNS CNAME mappings**
There is a 1:1 ratio for each load balancer endpoint to CNAME Record.

1. **gRPC CNAME** - maps the the gRPC endpoint(s) of your engine instance to your custom-domain. We recommend using `grpc-#` for your CNAME record.
2. **non-gRPC CNAME** - maps the the non-gRPC endpoint(s) of your engine instance to your custom-domain. We recommend using `non-grpc-#` for your CNAME record.
3. **console-ui CNAME** - maps the MDAI Engine™ Console within your engine instance to your custom-domain. You'll be able to access the endpoint <cname>.<your-domain>.<domain-suffix> _e.g., https://mydecisive-console.example.com/_

## Disable Engine

- Set replica count to `0` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 0
```

- `make config`
- `make install`

## Enable Engine

- Set replica count to `2` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 2
```

- `make config`
- `make install`

## Destroy the MDAI Engine™

Tired of using the MDAI Engine™? 😭 We're sorry to see you go, but we understand. If you have feedback for us, please fill out

## Generate and Collect telemetry

**What kind of user are you?**

1. I don't have any agents/collectors that I want to use at this time to send telemetry. Use Option 1!
2. I have sources of telemetry I'd love to send to my MDAI Engine™! Use Option 2!

### Option 1 - Use test data

1. Setup a Cronjob
2. Apply to cluster
3. See telemetry coming through
4. Delete the job after you're done

_It is critical that you delete the cronjob, otherwise engine costs will increase as throughput and processing power are resource intense._

> Note: This is a great option if you're not ready to commit to the costs associated with ingress/egress. It's all local to the cluster you have just deployed, so there will not be additional charges, minus the compute required to generate and process the telemetry.

### Option 2 - Use real data

1. Find the source of data (collector/agent) you'd like to point at your MDAI Engine™ instance
2. Use your CNAME (from your host provider) or DNS (from AWS LB)
3. Configure your agent/collector to point to the CNAME or DNS
4. SEE RESULTS! Go to Visualization step for more details.

## Visualize

Go to your AWS lb link

## Next steps
