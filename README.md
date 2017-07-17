# Kubernetes Initializer Tutorial

## Usage

Create a Kubernetes 1.7.0+ clusters with the alpha API enabled:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

## Tutorial

* [Deploy the Envoy Initializer](docs/deploy-envoy-initializer.md)
