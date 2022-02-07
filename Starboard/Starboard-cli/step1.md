# Overview & Installation

The Staboard CLI allow you to trigger scans and view the risks in a kubectl-compatible way or use Starboard as part of your CI/CD pipeline.
It is a single executable binary which can be used to find risks, such as vulnerabilities or insecure pod descriptors, in Kubernetes workloads. By default, the risk assessment reports are stored as instances of Custom Resource Definitions.

### Installation

You can find all installation options in the [documentation.](https://aquasecurity.github.io/starboard/v0.14.1/cli/)

In our case, we will install the kubectl plugin. This is done through a tool called Krew, which is already installed. 

```
kubectl krew install starboard
```{{execute}}

Make sure that the installation was successful:

```
kubectl starboard --version
```{{execute}}

Lastly, we have to run a one-time installation command. This will create a namespace for Starboard inside our cluster, which will keep our resports:

```
kubectl starboard install
```{{execute}}

Until we scan Kubernetes resources inside our cluster, this namespace will be empty:
```
kubectl get all -n starboard
```{{execute}}
