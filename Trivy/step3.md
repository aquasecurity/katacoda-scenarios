# Misconfiguration Scan

Trivy provides built-in policies to detect configuration issues in Docker, Kubernetes and Terraform. Also, you can write your own policies in Rego to scan JSON, YAML, HCL, etc.

### Scan your IaC files

Trivy can scan your IaC files for misconfigurations. The following command will check all IaC files in the repository at once:

```
trivy conf ./assets/examples/misconf/mixed/configs
```{{execute}}

Filter by the severity of the misconfiguration:

```
trivy conf --severity HIGH,CRITICAL ./assets/misconf/examples/mixed/configs
```{{execute}}

### Scan your Dockerfile for misconfigurations

Vulnerabilities can be introduced early into our workflow. Before deploying our containerised workloads, we want to make sure that the Dockerfile does not introduce any vulnerabilities.

Here is the Dockerfile that we are going to scan:

```
cat ./assets/examples/misconf/mixed/configs/Dockerfile
```{{execute}}

Let's scan it:

```
trivy conf ./assets/examples/misconf/mixed/configs/Dockerfile
```{{execute}}

