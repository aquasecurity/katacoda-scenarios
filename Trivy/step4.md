# Custom Policies

Write your own policies in Rego to scan JSON, YAML, HCL, etc.

### Compare multiple values from different files

We have the following deployment.yaml file and service.yaml file. Both files have some values such as the port in common. 

```
cat ./assets/examples/misconf/combine/configs/deployment.yaml
```

```
cat ./assets/examples/misconf/combine/configs/service.yaml
```

By setting the "combine": true flag, we can compare both files with Trivy.
This is done in the following custom policy example:

```
cat ./assets/examples/misconf/combine/policy/custom.rego
```

And when we run the trivy command, we can see that the service selector does not match the pod label

```
trivy conf --severity CRITICAL --policy ./assets/examples/misconf/combine/policy --namespaces user ./assets/examples/misconf/combine/configs
```

### Further examples with custom policies

In many cases, you want to make sure that only certain values are included in your configuration files.

For instance, in the following example, we want to make sure that certain ports are not exposed, this is done through the following files:

```
cat ./assets/examples/misconf/custom-data/policy/custom.rego ./assets/examples/misconf/custom-data/data/ports.yaml
```

We can then test our IaC resources for misconfiguration and whether or not any prohibited ports have been included:
```
trivy conf --severity HIGH,CRITICAL --policy ./assets/examples/misconf/custom-data/policy --data data --namespaces user ./assets/examples/misconf/custom-data/configs
```
