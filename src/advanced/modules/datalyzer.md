# Datalyzer Module

## Primary objective

Track and analyze the total and actual OpenTelemetry Protocol (OTLP) bytes transferred by each source (service/resource) through a collector.


## How it works

We built in a special OTLP Service that we export data to that allows us to understand the sender (by `service.name`) of a pLog, pMetric, and/or pTrace records, as well as measuring the payload size for each record that flow through your pipelines. 

This helps us answer your questions:
1. Who's sending the most data in and out of my cluster
2. How much are they sending in and planning to send out of my cluster?


## See it in action

1. Visit the Analysis tab in your console.
2. Send some payloads (real or fake).
3. See the sender and size of message in and out of your cluster!
4. Save money, eat cake instead! 🍰



