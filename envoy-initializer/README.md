# Envoy Initializer

The Envoy Initializer is a [Kubernetes initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects the [envoy](https://lyft.github.io/envoy) proxy into a pod based on policy.

## Usage

```
envoy-initializer -h
```
```
Usage of envoy-initializer:
  -annotation string
    	The annotation to trigger initialization (default "initializer.kubernetes.io/envoy")
  -configmap string
    	The envoy initializer configuration configmap (default "envoy-initializer")
  -initializer-name string
    	The initializer name (default "envoy.initializer.kubernetes.io")
  -namespace string
    	The configuration namespace (default "default")
  -require-annotation
    	Require annotation for initialization
```
