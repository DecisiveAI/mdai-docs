# ⏲️ Time for OpenTelemetry! 📈

Let's update your MDAI Cluster's OTel configuration file.

🤔 You've got a couple options...

## Option 1 - 👢 Bootstrap our built-in Collector Configuration

We have provided a default configuration for a simplified version of the OpenTelemetry collector at `values/otelcol-config.yaml`. Using our boilerplate can accelerate your deployment and configuration using OpenTelemetry.

*MOARRR CHOICES!*

You can...
1. Use the config as is and update at your will later
2. you can start making modifications right now

Learn more about the specifications for the [OTEL Collector](https://opentelemetry.io/docs/collector/) to make the best decisions for your telemetry pipelines configuration needs.


## Option 2 - 🧳 Bring Your Own Configuration
Want to use a custom or tried-and-true OTel configuration file that already works for you?

Simply update the configuration file at `templates/mdai-operator.yaml`.

----
<div class="left">
  <a href="./aws-env.md">⏪ Back to: AWS Env Config</a>
</div>
<div class="right">
  <a href="./initialize.md">Next Step: Initialize build ⏩</a><br /><br />
</div>
