# Summary
  [Overview](overview.md)
  [Disclaimer](DISCLAIMER.md)

# Introduction
  - [Architecture](./intro/architecture/architecture.md)
  - [The MDAI Cluster](./intro/intro.md)
  - [Pre-Alpha Expectations](./intro/expectations.md)

# Installation
  - [Supported Methods for Installing an MDAI Cluster](./install/installation.md)
  - [Local Install]()
    - [Quick Start](./install/local/quick-start.md)
    - [Prerequisites](./install/local/prerequisites.md)
    - [Installation](./install/local/install.md)
      - [Semi-automated Install](./install/local/semiautomated-install.md)
      - [Automated Install](./install/local/automated-install.md)
    - [Configure](./install/local/configure.md)
    - [Verify](./install/local/verify.md)
    - [Validate Data Flow](./install/local/validate.md)
    - [Life Cycle Management](./install/local/lifecycle/overview.md)
      - [Disable the MDAI Cluster](./install/local/lifecycle/disable-cluster.md)
      - [Enable the MDAI Cluster](./install/local/lifecycle/enable-cluster.md)
      - [Uninstall the MDAI Cluster](./install/local/lifecycle/uninstall.md)
    - [Testing your MDAI Cluster]()
      - [Generate and Collect Telemetry](./install/testing.md)
    - [Congrats!](./install/congrats.md)
  - [AWS Install]()
    - [Introduction](./install/aws/start.md)
    - [Prerequisites](./install/aws/prerequisites.md)
    - [AWS CLI](./install/aws/aws-cli.md)
    - [Check us out!](./install/aws/repo.md)
    - [AWS Config](./install/aws/aws-env.md)
    - [OTel Config](./install/aws/otel-config.md)
    - [Certificates](./install/aws/adding-certs.md)
    - [Apply Configs](./install/aws/apply-config.md)
    - [Deploy Your MDAI Cluster](./install/aws/deploy.md)
    - [Verify Installation](./install/aws/verify.md)
    - [Validate Installation](./install/aws/validate.md)
    - [UI Auth Options](./install/aws/ui-auth/options.md)
      - [Public Access](./install/aws/ui-auth/no-auth.md)
      - [Cognito](./install/aws/ui-auth/cognito.md)
      - [VPC](./install/aws/ui-auth/vpc.md)
    - [Life Cycle Management]()
      - [Overview](./install/aws/lifecycle/overview.md)
      - [Disable the MDAI Cluster](./install/aws/lifecycle/disable-cluster.md)
      - [Enable the MDAI Cluster](./install/aws/lifecycle/enable-cluster.md)
      - [Uninstall the MDAI Cluster](./install/aws/lifecycle/destroy-cluster.md)
    - [Testing your MDAI Cluster]()
      - [Generate and Collect Telemetry](./install/testing.md)

# Advanced Configuration
  - [MDAI Cluster Optimizations](./advanced/advanced.md)
    - [AutoScaling OTel Collector](./advanced/autoscaling/otel-col.md)
    - [Node AutoScaling](./advanced/autoscaling/node-autoscaling.md)

# Usage
  - [Using the MDAI Console](./usage/console/mdai-console.md)
  - [Modifying your OpenTelemetry Config](./usage/otel-updates.md)

# Troubleshooting
  - [Troubleshooting guide](./troubleshooting.md)
<!--
# Usage Guide

- [Installation](./install/install.md)
  - [To an existing k8s cluster](./install/k8s-helm.md)
  - [To a new AWS EKS cluster](./install/k8s-cdk.md)
- [Configuration](./Operation/config.md)
- [Troubleshooting](./troubleshooting.md)



#### Collector requirements

#### Sizing and Scaling


#### Processor Architecture



### Configure
### Install

- Installation instructions for deploying EKS locally or on-premises
- Setup instructions for OpenTelemetry and Prometheus components
- Basic configuration steps

-----------------------------------------------------------------------

## Contributing
- Guidelines for contributing code, documentation, or bug fixes
- Code repository location (e.g., GitHub)
- Contribution guidelines and code review process

## Community Engagement
- Links to community forums, mailing lists, or chat channels
- How to get support (e.g., FAQs, support tickets)
- Opportunities for community involvement

## Risk and Disclaimers
- Potential risks associated with using pre-alpha software
- Disclaimer about stability, data loss, and other issues
- Recommended backup and recovery procedures

## Legal and Licensing
- License information for the pre-alpha release
- Copyright notices and third-party dependencies
- Terms of use for early adopters

## Future Development
- Planned features and improvements for upcoming releases
- Roadmap for transitioning from pre-alpha to alpha/beta stages
- Community feedback integration process

## Glossary
- Definitions of technical terms and acronyms used in the documentation

## Appendices
- Additional resources for testers and contributors
- Release notes for the pre-alpha version
- Frequently Asked Questions (FAQs) specific to the pre-alpha release
-->
