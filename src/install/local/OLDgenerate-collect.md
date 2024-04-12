# Generate and Collect telemetry
----

1. Install OpenTelemetry's [telemetrygen](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/cmd/telemetrygen) utility.
   > ```@shell
   > go install github.com/open-telemetry/opentelemetry-collector-contrib/cmd/telemetrygen@latest
   > ```
2. Send Telemetry to the collector
   > ```@shell
   > $GOBIN/telemetrygen traces --otlp-insecure --traces 3
   > ```
3. _Optional: Add a cronjob to schedule telemetry at a cadence_
   > ```
   > TODO: command goes here!
   > ```

   ----
<span class="left"><a href="./setup.md">⏪ Back to Setup</a></span>
<span class="right"><a href="./validate.md">Next Step: Validate Data Flow ⏩</a></span>