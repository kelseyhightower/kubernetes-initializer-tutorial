# Kubernetes Initializer Tutorial

This tutorial walks you through building and deploying a [Kubernetes Initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects an [Envoy](https://lyft.github.io/envoy) proxy container into uninitialized Deployments. 

## Prerequisites

Kubernetes 1.7.0+ is required with [support for Initializers enabled](https://kubernetes.io/docs/admin/extensible-admission-controllers/#enable-initializers-alpha-feature). If you're using Google Container Engine create an alpha cluster:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

Download the tutorial by cloning this repository:

```
git clone https://github.com/kelseyhightower/kubernetes-initializer-tutorial.git
```

```
cd kubernetes-initializer-tutorial
```

## Tutorial

* [Deploy the Envoy Initializer](docs/deploy-envoy-initializer.md)
* [Initializing Deployments](docs/initializing-deployments.md)
* [Initializing Deployments Based on Metadata](docs/initializing-deployments-based-on-metadata.md)
* [Cleaning Up](docs/cleanup.md)
