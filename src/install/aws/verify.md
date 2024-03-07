### Verify the MDAI™ Engine
Ensure your cluster is up and running.
List all namespaces:
```shell
kubectl get ns
```
Expected output
![![img_5.png](../media/img_5.png)](../media/img_3.png)
```shell
kubectl get pods
```
Your output for default configuration should be similar to
![![img_4.png](../media/img_4.png)](../media/img_4.png)

### Configure Ingress for your MDAI Engine™

To securely setup ingress and external access to your MDAI Engine™, checkout our [Ingress](./ingress.md) documentation.
