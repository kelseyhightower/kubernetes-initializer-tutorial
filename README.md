# Kubernetes Initializer Tutorial

This tutorial will walk you through building and testing a [Kubernetes Initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers). The [Envoy Initializer](envoy-initializer) will be used to inject an [Envoy](https://lyft.github.io/envoy) proxy into an uninitialized Deployment. 

## Prerequisites

Kubernetes 1.7.0+ is required with [support for Initializers enabled](https://kubernetes.io/docs/admin/extensible-admission-controllers/#enable-initializers-alpha-feature). If you're using Google Container Engine create an alpha cluster:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

Download the tutorial artifacts by cloning this repository:

```
git clone https://github.com/kelseyhightower/kubernetes-initializer-tutorial.git
```

## Tutorial

* [Deploy the Envoy Initializer](docs/deploy-envoy-initializer.md)
* [Initializing Deployments](docs/initializing-deployments.md)
