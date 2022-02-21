# Installation

You can find all installation options in the [documentation](https://aquasecurity.github.io/trivy/v0.23.0/getting-started/installation/).

We are going to use the Ubuntu-based installation for this example. Upon starting the scenario, the following commands got executed in a script inside the terminal:

```
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```

Trivy should now be ready to go in your katacoda environment.

You can make sure that everything works through checking the Trivy version:
```
trivy --version
```{{execute}}


