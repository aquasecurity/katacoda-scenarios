# Scanning files and directories

## Scan local filesystem

With Trivy, you can also scan local projects including language-specific files.

This is done with the following command:

```
trivy fs [PATH-TO-YOUR-File]
```

In this example, we are going to use the go-app from the examples section in the Trivy repository, which is stored in this environment within the `assets` directory:

```
trivy fs ./assets/examples/misconf/go-testing
```{{execute}}

And again, you can use flags to filter for different information such as the severity of the vulnerabilities: 

```
trivy fs --severity HIGH,CRITICAL ./assets/examples/misconf/go-testing
```{{execute}}

## Scan Misconfigurations and Vulnerabilities 

You might have notices that the fs command only displays a list of vulnerabilities. However, you can check your filesystem for vulnerabilities and also misconfigurations by adding an additional flag:

```
trivy fs --security-checks config ./assets/examples/misconf/go-testing
```{{execute}}

## Scan remote repository

In many cases, we actually want to use someone else's repository for our own work. However, there are many risks involved in using just any repository.

With Trivy, you can scan a Git Repository. This is done with the `trivy repo` command:

```
trivy repo [URL_TO_REPOSITORY]
```

In our example, we are going to check the following repository for vulneratbilities:

```
trivy repo https://github.com/knqyf263/trivy-ci-test
```{{execute}}

**TASK**: Try it out with one of your Git repositories or your favourite open source poject

```
trivy repo [URL_TO_REPOSITORY]
```{{copy}}

## Scanning the root filesystem

With Trivy you can also scan a root filesystem (such as a host machine, a virtual machine image, or an unpacked container image filesystem).

This is done with the following command:

`trivy rootfs /path/to/rootfs`

```
trivy rootfs ../
```{{execute}}

Have a look at the different options:

```
trivy rootfs --help
```{{execute}}