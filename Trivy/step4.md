# Misconfiguration Scan

Trivy provides built-in policies to detect configuration issues in Docker, Kubernetes and Terraform. Also, you can write your own policies in Rego to scan JSON, YAML, HCL, etc.

"Rego was inspired by Datalog, which is a well understood, decades old query language. Rego extends Datalog to support structured document models such as JSON." [Source](https://www.openpolicyagent.org/docs/latest/policy-language/)

It basically allows you to define rules such as:
* Never allow the latest tag on container images
* Every pod needs to have its resource limits defined

### Scan your IaC files

Trivy can scan your IaC files for misconfigurations. 

You can scan either:
* An entire directory with multiple different types of IaC configurations e.g. Dockerfile and Terraform
* Specify a specific configuration file

The following command will check all IaC files in the repository at once:

```
trivy config [PATH_TO_CONFIG_FILES]
```

Try it out with our example:

```
trivy config ./assets/examples/misconf/mixed/configs
```{{execute}}

And again, you can filter by the severity of the misconfiguration:

```
trivy config --severity HIGH,CRITICAL ./assets/examples/misconf/mixed/configs
```{{execute}}

While the `fs` command scans language-specific filesystems, the `config` command will scan either specific IaC configuration files such as Dockefile but also directories containing multiple different configuration files such as Terraform and Dockerfile etc.

### Scan your Dockerfile for misconfigurations

Vulnerabilities can be introduced early into our workflow. Before deploying our containerised workloads, we want to make sure that the Dockerfile does not introduce any vulnerabilities.

Here is the Dockerfile that we are going to scan:

```
cat ./assets/examples/misconf/mixed/configs/Dockerfile
```{{execute}}

The cat command will just display the content of the file in the terminal.

Let's scan this dockerfile:

```
trivy config ./assets/examples/misconf/mixed/configs/Dockerfile
```{{execute}}

### Scan your Terraform configuration files for misconfigurations

"Terraform is an open-source infrastructure as code software tool that provides a consistent CLI workflow to manage hundreds of cloud services. Terraform codifies cloud APIs into declarative configuration files." [Source](https://www.terraform.io/)

Scanning our infrastructure for vulnerabilities and misconfigurations before deploying it is very powerful.

You can scan your terraform resources through the same command by specifying the directory with your terraform configuration files:

```
trivy config ./assets/examples/misconf/mixed/configs/terraform
```{{execute}}