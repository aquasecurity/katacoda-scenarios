# Installing the Starboard Operator

In this example, we are going to install the Starboard Operator through kubectl. Alternatively, you could use [Helm](https://aquasecurity.github.io/starboard/v0.14.1/operator/installation/helm/) or the [Operator Lifecycle Manager](https://aquasecurity.github.io/starboard/v0.14.1/operator/installation/olm/). 

To follow the next steps, you have to make sure to follow each step below to install the operator.

Send custom resource definitions to the Kubernetes API:

```
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/crd/vulnerabilityreports.crd.yaml \
  -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/crd/configauditreports.crd.yaml \
  -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/crd/clusterconfigauditreports.crd.yaml \
  -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/crd/ciskubebenchreports.crd.yaml
```

Next, send the following Kubernetes object definitions to the Kubernetes API:

```
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/static/01-starboard-operator.ns.yaml \
  -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/static/02-starboard-operator.rbac.yaml
```


## Customise configurations -- Optional

Create the starboard ConfigMap and the starboard secret in the starboard-system namespace. This will become handy when Starboard is used in combination with Trivy or Aqua Enterprise:

```
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/static/03-starboard-operator.config.yaml
```

Review the default values and make sure the operator is configured properly:

```
kubectl describe cm starboard starboard-trivy-config starboard-polaris-config -n starboard-system
```

You can make any changed to the configmap through the following command:
```
kubectl edit cm starboard starboard-trivy-config starboard-polaris-config -n starboard-system
```

## Create the Starboard Kubernetes Operator inside the cluster

Finally, create the starboard-operator Deployment in the starboard-system namespace to start the operator's pod:

```
kubectl apply -f https://raw.githubusercontent.com/aquasecurity/starboard/v0.14.1/deploy/static/04-starboard-operator.deployment.yaml
```

To confirm that the operator is running, check the number of replicas created by the starboard-operator Deployment in the starboard-system namespace:

```
kubectl get deployment -n starboard-system
```

