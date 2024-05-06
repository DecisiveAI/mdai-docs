## Disable Nucleus

- Set replica count to `0` in `values/params-values-otel.yaml`:

```yaml
spec:
  # 2 replicas recommended
  replicas: 0
```

- `make config`
- `make install`
