## Deploying to AWS

**💪 You're ready to deploy your MDAI Engine™ instance! 💪**

Ready to see the Engine in action?
<div class="warning">
  Note: After deploying, the engine will be active and running in AWS. There are costs associated with running our engine, however, we've done all we can to make the infrastructure as cost-effective as possible
</div>

### Deploy the MDAI™ Engine

```shell
make install
```
- Install will check and bootstrap the CDK Toolkit if it's not present for the region.
![[img.png](../media/img.png)](../media/img.png)
- CDK will output the detected changes and ask to accept or reject the changes. Review carefully before proceeding.
![![img_1.png](../media/img_1.png)](../media/img_1.png)
- Follow the progress of the stack creation through the terminal
![![img_2.png](../media/img_2.png)](../media/img_2.png)
or AWS Console -> Cloud Formation
![![img_3.png](../media/img_3.png)](../media/img_3.png)
- The installation process will add a new context to your `kubeconfig`. You can switch context by running `kubectl config use-context <desired_context>`
Detailed output stored into `cdk-output.json`.

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

To securely setup ingress and external access to your MDAI Engine™ instance, use our [Ingress configuration guide](./ingress.md).
