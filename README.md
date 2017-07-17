# Kubernetes Initializer Tutorial

This tutorial will walk you through building and testing a [Kubernetes Initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers). The [Envoy Initializer](envoy-initializer) will be used to inject an [Envoy](https://lyft.github.io/envoy) proxy into uninitialized Deployments. 

## Prerequisites

Kubernetes 1.7.0+ is required with [support for Initializers enabled](https://kubernetes.io/docs/admin/extensible-admission-controllers/#enable-initializers-alpha-feature). If you're using Google Container Engine create an alpha cluster:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

## Tutorial

* [Deploy the Envoy Initializer](docs/deploy-envoy-initializer.md)
* [Initializing Deployments](docs/initializing-deployments.md)
