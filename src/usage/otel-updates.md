# Updating OpenTelemetry Configurations

If you find you'd like to modify your OpenTelemetry collector configuration, you have the option to change it. 

### Modify your OTel Config

Navigate to the `lib/mdai-operator.yaml` file and modify it to fit your needs.

### Apply changes to your collector

You can now apply them to the cluster using the following command. 

```bash
kubectl apply -f lib/mdai-operator.yaml
```

You should start seeing changes reflected immediately in the Console UI.