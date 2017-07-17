# Kubernetes Initializer Tutorial

This tutorial will walk you through building and testing a [Kubernetes Initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers). The [Envoy Initializer](envoy-initializer) will be used to inject an [Envoy](https://lyft.github.io/envoy) proxy into uninitialized pods. 

## Prerequisites

Create a Kubernetes 1.7.0+ clusters with the alpha API enabled. If you're using Google Container Engine create an alpha cluster:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

## Tutorial

* [Deploy the Envoy Initializer](docs/deploy-envoy-initializer.md)
* [Initializing Pods](docs/initializing-pods.md)
