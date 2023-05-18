# kubecub
kubecub provides chain capability for Kubernetes.
## Introduction
kubecub enables you to chain multiple Kubernetes resources together. You can create dependencies between pods, configmaps, secrets, and more - and kubecub will ensure they are applied to your cluster in the correct order.
Some use cases for kubecub include:
- Applying CRDs before creating CRs
- Creating secrets/configmaps before pods that mount them as volumes
- Having jobs run before other resources that depend on them
kubecub uses the Kubecub custom resource to define chains. Each chain consists of multiple links, where each link points to a Kubernetes resource or external URL.
## Getting Started
To get started with kubecub:
1. Install kubecub into your Kubernetes cluster using the deployment YAML.
2. Define a Kubecub CR with your chain links:
```yaml
apiVersion: kubecub.example.com/v1 
kind: Kubecub
metadata:
  name: my-chain
spec:
  links:
  - name: link1 
    resource: pod/mypod
  - name: link2
    resource: secret/mysecret 
  - name: link3 
    url: https://example.com/configmap.yaml 
```
3. Apply the Kubecub CR. kubecub will process the links in order and apply/download the resources.
4. Check the status of your chain to ensure all links have been successfully applied.
kubecub allows you to build complex dependency chains across all of your Kubernetes resources and external files. Let me know if you have any other questions!
The default branch for this project is main.
