# ArgoCD workthroughs

This repository contains example applications for demoing ArgoCD functionality. 

Feel free to register this repository to your ArgoCD instance, or fork this repo and push your own commits to explore ArgoCD and GitOps!

## Prerequisites
- A Kubernetes cluster running version 1.16 or later
- [kubectl](https://kubernetes.io/docs/tasks/tools/) installed and configured to access your Kubernetes cluster
- [helm](https://helm.sh/docs/intro/install/) installed
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) installed and running
- [Argo Workflows](https://argoproj.github.io/argo-workflows/) installed and running
- [Argo Events](https://argoproj.github.io/argo-events/) installed and running
- [Argo Rollouts](https://argoproj.github.io/argo-rollouts/) installed and running
- [jsonnet](https://jsonnet.org/) installed
- [kustomize](https://kubernetes-sigs.github.io/kustomize/) installed
- [jq](https://stedolan.github.io/jq/) installed



[![ArgoCD](https://argo-cd.readthedocs.io/en/stable/assets/logo.png)](https://github.com/argoproj/argo-cd)


# Introduction

jsonnet is a data-templating language that allows you to generate JSON or YAML files. It is particularly useful for generating Kubernetes manifests, as it allows you to define your resources in a more modular and reusable way.
jsonnet is a powerful tool for generating Kubernetes manifests, and it can be used in conjunction with ArgoCD to manage your Kubernetes applications. In this repository, we will explore how to use jsonnet with ArgoCD to manage your Kubernetes applications.
# Getting Started
## Prerequisites
- [yq](



| Application | Description |
|-------------|-------------|
| [hello-world](01-helloworld/) | A hello word guestbook app as plain YAML |
| [helm-guestbook](02-helm-guestbook/) | The guestbook app as a Helm chart |
| [jsonnet-guestbook](jsonnet-guestbook/) | The guestbook app as a raw jsonnet |
| [jsonnet-guestbook-tla](jsonnet-guestbook-tla/) | The guestbook app as a raw jsonnet with support for top level arguments |
| [kustomize-guestbook](kustomize-guestbook/) | The guestbook app as a Kustomize 2 app |
| [pre-post-sync](pre-post-sync/) | Demonstrates Argo CD PreSync and PostSync hooks |
| [sync-waves](sync-waves/) | Demonstrates Argo CD sync waves with hooks |
| [helm-dependency](helm-dependency/) | Demonstrates how to customize an OTS (off-the-shelf) helm chart from an upstream repo |
| [sock-shop](sock-shop/) | A microservices demo app (https://microservices-demo.github.io) |
| [plugins](plugins/) | Apps which demonstrate config management plugins usage |
| [apps](apps/) | An app composed of other apps |
