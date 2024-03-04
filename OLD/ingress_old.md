There are three entry points to the engine:

1. **gRPC Load Balancer Endpoint** - enables gRPC telemetry to be sent to the engine.
2. **http Load Balancer Endpoint** - enables http telemetry to be sent to the engine
3. **console-ui Load Balancer Endpoint** - serves the MDAI Console for monitoring your engine instance

In order to enable access allowed external access to the engine, you need to do the following:

**Identify the Load Balancer DNS names**

1. In the AWS Console, navigate to your [EC2 Load Balancers endpoints](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#LoadBalancers) _Note: link above take you to region: us-east-1, you will need to change if you've deployed your engine in a different region_
2. Locate the three load balancers required to run an MDAI Engine™, there should be a gRPC, http, and console-ui load balancer. Make note of each of the load balancer's DNS names. ![![load balancers](../media/load-balancers.png)](../media/load-balancers.png)

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
