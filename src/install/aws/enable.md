## Enable Nucleus

- Set replica count to `2` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 2
```

- `make config`
- `make install`
