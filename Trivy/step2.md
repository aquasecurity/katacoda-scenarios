# Vulnerability Scanning

### Image Scanning

Check a container image for vulnerabilities:

```
trivy image node:17.4.0-alpine
```{{execute}}


You can pass in additional flags depending on your needs:

```
trivy image --help
```{{execute}}


### Scanning files and directories

Scan a local project including language-specific files:

```
trivy fs ./assets/examples/misconf/go-testing
```{{execute}}

Scan Git Repository
```
trivy repo https://github.com/knqyf263/trivy-ci-test
```{{execute}}

### Scanning the root filesystem

With Trivy you can also scan a root filesystem (such as a host machine, a virtual machine image, or an unpacked container image filesystem).

This is done with the following command:

`trivy rootfs /path/to/rootfs`

Have a look at the different options:

```
trivy rootfs --help
```{{execute}}