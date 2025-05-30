# GitOps along with ArgoCD Workthroughs

[![ArgoCD logo: stylized orange and blue robot with a friendly expression, standing on a blue circular background. The robot is smiling, conveying a welcoming and approachable tone. The wider environment is a clean, minimalistic design with no additional text or elements.](./assets/workflow.png)](https://argo-cd.readthedocs.io/en/stable/)

This repository provides example applications for demonstrating ArgoCD functionality and GitOps principles.


Think of this as a hands-on playground for learning and experimenting with ArgoCD.


You can use it to:
* Set up your own infrastructure repository for deploying applications to Kubernetes.
* Learn how to use ArgoCD and GitOps to manage your Kubernetes applications.
* Explore practical examples for building your own GitOps pipelines.

The applications in this repository are intended for demonstration purposes, not production use. They showcase effective methods for managing Kubernetes applications with ArgoCD and GitOps.

Feel free to register this repository with your ArgoCD instance, or fork it and experiment by pushing your own commits to explore ArgoCD and GitOps.


# Introduction

This section provides an overview of the tools and technologies used in this repository, including ArgoCD, Jsonnet, Kustomize, Helm, and GitOps, and how they work together to manage Kubernetes applications.

- [**YAML**](https://yaml.org/) is a human-readable data serialization format commonly used for configuration files and data exchange between languages. It is often used in conjunction with Kubernetes to define resources and configurations in a structured manner. YAML's simplicity and readability make it a popular choice for defining Kubernetes manifests, allowing developers to easily understand and modify configurations.   

- [**Kubernetes**](https://kubernetes.io/) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It provides a robust framework for managing complex applications in a distributed environment, enabling developers to focus on building applications rather than managing infrastructure.

- [**kubectl**](https://kubernetes.io/docs/tasks/tools/) is the command-line tool for interacting with Kubernetes clusters. It allows you to manage and deploy applications, inspect cluster resources, and perform administrative tasks. Kubectl is essential for working with Kubernetes, as it provides a powerful interface for managing your cluster and its resources.

- [**Helm**](https://helm.sh/) is a package manager for Kubernetes that simplifies the deployment and management of applications. It uses charts, which are pre-configured packages of Kubernetes resources, to streamline application installation and upgrades. Helm's templating capabilities allow for dynamic configuration, making it a popular choice for managing complex applications in Kubernetes.

- [**GitOps**](https://www.gitops.tech/) is a set of practices that uses Git as the single source of truth for declarative infrastructure and applications. It enables teams to manage their Kubernetes resources using Git repositories, allowing for version control, collaboration, and automated deployments. GitOps promotes a clear separation between application code and infrastructure, making it easier to manage complex deployments and ensuring consistency across environments.

- [**ArgoCD**](https://argo-cd.readthedocs.io/en/stable/) is a declarative, GitOps continuous delivery tool for Kubernetes. It enables you to manage your Kubernetes applications using Git repositories as the source of truth. ArgoCD automates the deployment and synchronization of applications, ensuring that your cluster state matches the desired state defined in your Git repository.

- [**Argo Workflows**](https://argoproj.github.io/argo-workflows/) is a Kubernetes-native workflow engine for orchestrating parallel jobs. It allows you to define complex workflows as Kubernetes resources, enabling you to automate tasks such as CI/CD pipelines, data processing, and machine learning workflows.

- [**Argo Events**](https://argoproj.github.io/argo-events/) is an event-driven framework for Kubernetes that enables you to trigger workflows and actions based on events from various sources. It allows you to create event-driven architectures by integrating with external systems, such as webhooks, message queues, and cloud services.

- [**Argo Rollouts**](https://argoproj.github.io/argo-rollouts/) is a Kubernetes controller and set of CRDs that provide advanced deployment capabilities, such as blue-green and canary deployments. It allows you to manage the rollout of new application versions with fine-grained control, enabling safer and more reliable updates.

- [**Argo CD Notifications**](https://argocd-notifications.readthedocs.io/en/stable/) is a notification engine for ArgoCD that allows you to send notifications based on events in your ArgoCD applications. It supports various notification channels, such as email, Slack, and webhooks, enabling you to stay informed about the status of your applications and deployments.

- [**Argo CD App of Apps**](https://argo-cd.readthedocs.io/en/stable/operator-manual/app-of-apps/) is a pattern for managing multiple ArgoCD applications using a single parent application. This approach allows you to define a hierarchy of applications, making it easier to manage complex deployments and dependencies between applications. The App of Apps pattern enables you to treat your entire application ecosystem as a single unit, simplifying deployment and management.


- [**Kustomize**](https://kubernetes-sigs.github.io/kustomize/) is a powerful tool for customizing Kubernetes YAML configurations. It allows you to create overlays, manage patches, and define reusable components, making it easier to manage complex deployments. Kustomize is built into `kubectl`, enabling seamless integration with Kubernetes workflows.


- [**Jsonnet**](https://jsonnet.org/) is a powerful data templating language that enables you to define complex configurations and generate JSON or YAML files. It excels at producing Kubernetes manifests by allowing you to create modular, reusable components, define functions, and manage dependencies. This leads to cleaner, more maintainable configurations, especially for complex deployments. 
Jsonnet's ability to abstract and parameterize manifest generation makes it an ideal tool for managing Kubernetes resources, and when used with ArgoCD, it enables robust and automated application deployments.
In this repository, we will explore how to use Jsonnet with ArgoCD to manage your Kubernetes applications.

- [**jq**](https://stedolan.github.io/jq/) is a lightweight and flexible command-line JSON processor. It allows you to slice, filter, map, and transform structured data in JSON format. jq is particularly useful for parsing and manipulating JSON data, making it an essential tool for working with APIs, configuration files, and data processing tasks. Its powerful querying capabilities enable users to extract specific information from complex JSON structures quickly.


# Getting Started

## Prerequisites
- A Kubernetes cluster running version 1.16 or later
- [kubectl](https://kubernetes.io/docs/tasks/tools/) installed and configured to access your Kubernetes cluster
- [helm](https://helm.sh/docs/intro/install/) installed
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) installed and running
- [Argo Workflows](https://argoproj.github.io/argo-workflows/) optionsally installed and running
- [Argo Events](https://argoproj.github.io/argo-events/) installed and running
- [Argo Rollouts](https://argoproj.github.io/argo-rollouts/) installed and running
- [jsonnet](https://jsonnet.org/) installed
- [kustomize](https://kubernetes-sigs.github.io/kustomize/) installed
- [jq](https://stedolan.github.io/jq/) installed


## Table of Contents

| Application | Description |
|-------------|-------------|
| [hello-world](01-helloworld/) | A helloworld app (inspectorgadget) as plain YAML |
| [helm-helloworld](02-helm-helloworld/) | A helloworld app (inspectorgadget) app as a Helm chart |
| [pov](03-pov/) | A Persistent Volume Claim to be used for a ngnix web application |
| [apps](04-apps/) | An app composed of other apps |
| [gnx-apps](05-gnx-apps/) | A full fladge microservice app composed of other apps |
| [jsonnet-helloworld](06-jsonnet-helloworld/) | The helloworld app as a raw jsonnet |
| [jsonnet-guestbook-tla](jsonnet-guestbook-tla/) | The guestbook app as a raw jsonnet with support for top level arguments |
| [kustomize-guestbook](kustomize-guestbook/) | The guestbook app as a Kustomize 2 app |
| [pre-post-sync](pre-post-sync/) | Demonstrates Argo CD PreSync and PostSync hooks |
| [sync-waves](sync-waves/) | Demonstrates Argo CD sync waves with hooks |
| [helm-dependency](helm-dependency/) | Demonstrates how to customize an OTS (off-the-shelf) helm chart from an upstream repo |
| [genocs-shop](sock-shop/) | A microservices demo app based on [genocs-library](https://github.com/Genocs/genocs-library) |
| [plugins](plugins/) | Apps which demonstrate config management plugins usage |


## 01. Helloworld
Is a simple hello world application that demonstrates how to use ArgoCD to deploy an application as plain YAML. The application is the `inspectorgadget` application that allows users to view the web server configuration.

## 02. Helm-Helloworld
Is a simple hello world application that demonstrates how to use ArgoCD to deploy a Helm chart. The application is the `inspectorgadget` application that allows users to view the web server configuration.

## 03. PVC
Is a simple application that demonstrates how to use ArgoCD to deploy a Persistent Volume Claim (PVC). The PVC is created using a StorageClass that is defined in the Kubernetes cluster.

## 04. Apps
Is a microservice application that demonstrates how to use ArgoCD to deploy an application composed of a set of services. The Images are publicly available on Docker Hub. The application is the common used Genocs Library Microservice application. 
The application is composed of the following services:

----
>
> This repository is a work in progress and will be updated with more examples and applications over time. If you have any questions or suggestions, please feel free to open an issue or pull request.
>

# Dapr
[![Dapr Logo](./assets/Dapr_logo.svg)](https://Dapr.io)


[**Dapr**](https://dapr.io) (Distributed Application Runtime) is an open-source project that provides a set of building blocks for developing microservices applications. It simplifies the development of distributed applications by providing a set of APIs and runtime components that can be used to build, deploy, and manage microservices.
Dapr provides a set of building blocks that can be used to build microservices applications, including:
- *Service invocation*: Dapr provides a simple API for invoking services, allowing developers to easily call other services in their application.
- *State management*: Dapr provides a simple API for managing state, allowing developers to easily store and retrieve state in their application.
- *Pub/sub messaging*: Dapr provides a simple API for sending and receiving messages, allowing developers to easily communicate between services in their application.
- *Bindings*: Dapr provides a simple API for integrating with external systems, allowing developers to easily connect their application to external services.
- *Secrets management*: Dapr provides a simple API for managing secrets, allowing developers to easily store and retrieve secrets in their application.
- *Observability*: Dapr provides a simple API for collecting metrics and logs, allowing developers to easily monitor their application.
- *Distributed tracing*: Dapr provides a simple API for collecting distributed traces, allowing developers to easily trace requests through their application.
- *Resiliency*: Dapr provides a simple API for implementing resiliency patterns, allowing developers to easily handle failures in their application.
- *Actor model*: Dapr provides a simple API for implementing the actor model, allowing developers to easily build applications using the actor model.
- *Sidecar architecture*: Dapr uses a sidecar architecture, allowing developers to easily integrate Dapr into their existing applications without modifying the application code.
- *Language agnostic*: Dapr is language agnostic, allowing developers to use any programming language to build their applications.
- *Platform agnostic*: Dapr is platform agnostic, allowing developers to run their applications on any platform, including Kubernetes, VMs, and bare metal.
- *Cloud agnostic*: Dapr is cloud agnostic, allowing developers to run their applications on any cloud provider, including AWS, Azure, and Google Cloud.
- *Open source*: Dapr is an open source project, allowing developers to contribute to the project and use it in their applications without any licensing fees.
- *Community driven*: Dapr is a community driven project, allowing developers to contribute to the project and use it in their applications without any licensing fees.
- Dapr is:
  - Extensible
  - Modular
  - Lightweight
  - Fast
  - Scalable
  - Secure
  - Reliable
  - Flexible
  - Easy to use
  - Easy to learn
  - Easy to integrate
  - Easy to deploy
  - Easy to manage
  - Easy to monitor
  - Easy to debug
  - Easy to test

> **NOTE**:
>
> One of the main concern developers have when building Dapr application is:
> **how to leverage the debug capability provided by Visual Studio?** 

One easy solution is to use a Visual Studio Code extension called [Dapr Debugger](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-dapr). Even though this extension comes with a lot of features, it is not the only way to debug Dapr applications. In this section, we will explore how to debug Dapr applications using Visual Studio and Visual Studio Code.

>
> The Dapr Debugger extension is in preview and is not yet fully supported. 
> However, it is a great tool for debugging Dapr applications and provides a lot of features that can help you debug your applications.
>

## Debugging Dapr applications using Visual Studio

### Prerequisites
- WIP

