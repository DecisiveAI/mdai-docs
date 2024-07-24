# Using curl or grpcurl to send data to MDAI Cluster

# OTLP JSON request examples

Our InkOps repo has an [example directory](https://github.com/DecisiveAI/mdai-inkops/tree/main/examples) containing
* OTLP JSON files for all signals (MLT) that can be used as request payloads
* GRPC Service Definitions to use for grpcurl requests

The [README.md](https://github.com/DecisiveAI/mdai-inkops/blob/main/examples/README.md) has extensive documentation for local testing, however, this guide is more up-to-date.


## Sending a curl

Send a `curl` request to the collector (e.g. for Logs):

```shell
# Set OTLP endpoint
export OTLP_ENDPOINT=HOST:PORT

# execute the request using the data from the example log data file
curl -X POST -H "Content-Type: application/json" -d @./examples/http_service/logs.json -i http://${OTLP_ENDPOINT}/v1/logs
```

You can also send a gcurl request to the collector (e.g. for Logs):

## Sending a grpcurl

### Pre-req Install grpcurl

Find your method for downloading using their [Installation Guide](https://github.com/fullstorydev/grpcurl)

or 

Via homebrew
```shell
brew install grpcurl
```


### Send a request

```shell
# Set OTLP endpoint - Be sure to chance your-domain.io to your domain where a cert exists (This should've been done during setup)
export OTLP_ENDPOINT=otlp.grpc.endpoint.collector.your-domain.io:443

# use data from ./examples/grpc_service/logs.json AND
# run the request using the data (as stdin) copied from above
```shell
cat ./examples/grpc_service/logs.json |
grpcurl -vv -insecure \
    -d @ \
    -proto examples/protos/opentelemetry/proto/collector/logs/v1/logs_service.proto \
    -import-path examples/protos \
    $OTLP_ENDPOINT \
    opentelemetry.proto.collector.logs.v1.LogsService/Export
```

> Note: Remember to change the Service path and Service Namespace when sending other signals (traces/metrics).

<br />
<br />
<br />
----

## Coming from Local Install?

<span class="left" style="width: 50%">
  <a href="./local/testing.md">⏪ Back to Sending Data to MDAI</a>
</span>
<span class="right" style="width: 50%">
  <span>Want to validate telemetry data flowing through your pipelines?</span>
  <br />
  <a href="./local/validate.md">Next Step: Validate ⏩</a>
  <br />
  <br />
  <span>Know how to validate data flow already?</span>
  <a href="congrats.md">Next Step: Congrats! ⏩</a>
</span>

<br />
<br />
<br />
<br />
<br />

## Coming from AWS Install?

<div>
  <span class="left" style="width: 50%">
    <a href="./aws/verify.md">⏪ Back to Verify Installation</a>
  </span>
  <span class="right" style="width: 50%">
    <span>Want to validate telemetry data flowing through your pipelines?</span>
    <br />
    <a href="./aws/validate.md">Next Step: Validate ⏩</a>
    <br />
    <br />
    <span>Know how to validate data flow already?</span>
    <a href="congrats.md">Next Step: Congrats! ⏩</a>
  </span>
</div>
