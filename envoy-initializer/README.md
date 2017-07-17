# Envoy Initializer

The Envoy Initializer is a [Kubernetes initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects the [envoy](https://lyft.github.io/envoy) proxy into a pod based on policy.

## Usage

```
envoy-initializer -h
```
```
Usage of envoy-initializer:
  -configmap string
    	The envoy-initializer configmap name (default "envoy-initializer")
  -initializer-name string
    	Set the initializer name (default "envoy.initializer.kubernetes.io")
  -namespace string
    	The Kubernetes namespace (default "default")
```
