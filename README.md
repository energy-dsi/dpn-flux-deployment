# dpn-flux-deployment

This repository contains the deployment configuration for the DPN Flux application. The deployment configuration is managed using [Helm](https://helm.sh/). 
Helm is a package manager for Kubernetes that allows you to define, install, and upgrade Kubernetes applications.

## Prerequisites
To deploy the DPN Flux application, you will need the following tools installed on your local machine:
- [Helm](https://helm.sh/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Flux CLI](https://fluxcd.io/flux/installation/)

## Flux Bootstrap
Install the Flux controllers
The recommended way of installing Flux on Kubernetes clusters is by using the bootstrap procedure.

## Bootstrap with Flux CLI
The flux `bootstrap` command deploys the Flux controllers on Kubernetes cluster(s) and configures the controllers to sync the cluster(s) state from a Git repository. 
Besides installing the controllers, the bootstrap command pushes the Flux manifests to the Git repository and configures Flux to update itself from Git.

The flux bootstrap github command deploys the Flux controllers on a Kubernetes cluster and configures the controllers to sync the cluster state from a GitHub repository. Besides installing the controllers, the bootstrap command pushes the Flux manifests to the GitHub repository and configures Flux to update itself from Git.

After running the bootstrap command, any operation on the cluster (including Flux upgrades) can be done via Git push, without the need to connect to the Kubernetes cluster.

### To bootstrap Flux, the person running the command must have cluster admin rights for the target Kubernetes cluster. It is also required that the person running the command to be the owner of the GitHub repository, or to have admin rights of a GitHub organisation.

```
  flux bootstrap git \
  --url=ssh://git@github.com/<org>/<repository> \
  --branch=<my-branch> \
  --private-key-file=<path/to/ssh/private.key> \
  --password=<key-passphrase> \
  --path=clusters/my-cluster`
```