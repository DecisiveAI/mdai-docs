# Troubleshooting

## K8s

### The MyDecisive Engine pods are restarting repeatedly or fail to run in my K8s cluster

Your cluster may lack sufficient resources to run the engine along with the current workload the cluster is running. Check out [this article](#).

## AWS

### I tried to deploy the [CDK App](/src/Installation.md#deploy-a-new-eks-cluster-with-aws-cdk), but an error occurred and the EKS cluster was not deployed

Check to ensure that you have sufficient permissions to provision an EKS cluster by checking [the EKS documentation](#)
