# Welcome to Starboard!

In short, Starboard is a Kubernetes-native security toolkit.

This tutorial will focus on using the Starboard CLI.

You can find the details in the documentation.

Alternatively, Starboard also comes as Kubernetes Operator, which we explore in another tutorial:
* [Katacoda Tutorial for the Starboard Operator](https://github.com/aquasecurity/katacoda-scenarios/tree/main/Starboard/Starboard-operator) 
* [Starboard Operator Documentation](https://github.com/aquasecurity/starboard-operator)

## Overview

Starboard provides:

* Automated vulnerability scanning for Kubernetes workloads.
* Automated configuration audits for Kubernetes resources with predefined rules or custom Open Policy Agent (OPA) policies.
* Automated infrastructures scanning and compliance checks with CIS Benchmarks published by the Center for Internet Security (CIS).
* Penetration test results for a Kubernetes cluster.
* Custom Resource Definitions and a Go module to work with and integrate a range of security scanners.
* The Octant Plugin and the Lens Extension that make security reports available through familiar Kubernetes interfaces.


## About this scenario

This scenario will show you how to use the Starboard CLI to scan your deployments for vulnerabilities.

We will
* Install Krew to then install the Kubernetes Starboard kubectl-plugin
* Deploy nginx 
* Scan our deployment with the kubectl starbpard plugin for vulnerabilities

You will not need to install anything locally or from an external website, everything is provided through Katacoda. However, you are encouraged to play around with with the example once the scenario is over.

## Resources

* [Website]() -- Coming Soon!
* [GitHub](https://github.com/aquasecurity/starboard)
* [Documentation](https://aquasecurity.github.io/starboard/)

## Questions

If you have any questions, please join the [Aqua Slack channel](https://slack.aquasec.com/). 

