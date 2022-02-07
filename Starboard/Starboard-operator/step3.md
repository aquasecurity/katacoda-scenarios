# Infrastructure Scans 

Similar to how the operator detects and scans deployments in your Kubernetes cluster automatically, it also discovers Kubernetes nodes and runs CIS Kubernetes Benchmark checks on each of them. The results are stored as CISKubeBenchReport objects. In other words, for a cluster with 3 nodes the operator will eventually create 3 benchmark reports: 

Check how many nodes are part of your cluster:

```
kubectl get nodes
```{{execute}}

You should find an equal number of ciskubebenchreports:

```
kubectl get ciskubebenchreports -o wide
```{{execute}}

Notice that each CISKubeBenchReport is named after a node and is controlled by that node to inherit its life cycle:

```
kubectl tree node kind-control-plane -A
```{{execute}}