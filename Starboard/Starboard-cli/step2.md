# Scan Kubernetes Deployment 

Before we can scan new Kubernetes deployments, we need deployments.

For this, we are going to create a new namespace:

```
kubectl create namespace nginx
```

Let's install an older version of nginx that has vulnerabilities:

```
kubectl create deployment nginx --image nginx:1.16 -n nginx
```

We can view our deployment with the following command:

```
kubectl get all -n nginx
```

### Scan your Deployment

Finally, we can scan our nginx deployment:

```
kubectl starboard scan vulnerabilityreports deployment/nginx -n nginx
```


### Access Reports

The reports of your security scan are kept in the starboard namespace inside of your Kubernetes cluster.

You can access the report through the following command:

```
kubectl starboard get vulnerabilityreports deployment/nginx --container nginx -o yaml -n nginx
```

Basically, an object called Vulnerabilityreports is created inside the namespace of the deployment.
This object holds the outcome of the scan. You can find the reports through the following commands:

```
kubectl get Vulnerabilityreports -n nginx 
```

And then select the report that you want to display:
```
kubectl get Vulnerabilityreports/{name of the report} -o yaml -n nginx
```

Lastly, you could also access the report as a html page.

First, save the report in an html file:

```
kubectl starboard report deployment/nginx > nginx.deploy.html
```

You could then open the file through:

```
open nginx.deploy.html
```
