# ⏲️ Time to Configure OpenTelemetry! 📈

> **Warning:** ⚠️ This configuration method is deprecated ⚠️   
New documentation how to use mdai operator configuration instead is coming soon.
   
   
Let's update your MDAI Cluster's OTel configuration file.

🤔 You've got a couple options...

## Option 1 - 👢 Bootstrap our built-in Collector Configuration

We have provided a default configuration for a simplified version of the OpenTelemetry collector at `values/otelcol-config.yaml`. Using our boilerplate can accelerate your deployment and configuration using OpenTelemetry.

*MOARRR CHOICES!*

You can...
1. Use the config as is to accelerate through configuration
2. Making modifications right now that better fit your pipeline needs

Learn more about the specifications for the [OTEL Collector](https://opentelemetry.io/docs/collector/) to make the best decisions for your telemetry pipelines configuration needs.


## Option 2 - 🧳 Bring Your Own Configuration
Want to use a custom or tried-and-true OTel configuration file that already works for you?

Simply update the configuration file at `values/otel-config.yaml`.


## Apply change

After you've configured you OTel pipelines to your heart's desire, you can apply your changes by running

```shell
# Update config file within the cluster directory, it will get applied to your cluster instance automatically via a k8s operator.
kubectl apply -f values/otel-config.yaml
```

----
<span class="left"><a href="./install.md">⏪ Back to Install</a></span>
<span class="right"><a href="./verify.md">Next Step: Verify ⏩</a></span>

