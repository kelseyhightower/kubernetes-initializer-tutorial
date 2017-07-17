# Deploy the Envoy Initializer

The Envoy Initializer is a [Kubernetes initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects the [envoy](https://lyft.github.io/envoy) proxy into a pod based on policy.

## Install

### Store the envoy config in a ConfigMap

The envoy proxy requires a [configuration file](https://lyft.github.io/envoy/docs/configuration/configuration.html) before it can be used to forward traffic to other containers in a pod. Store the default `envoy.json` configuration in a configmap:

```
kubectl create configmap envoy --from-file envoy.json
```

### Create the envoy-initializer ConfigMap 

The `envoy-initializer` is configured using a ConfigMap, identified by the `-configmap` flag, which provides the containers and volumes to inject into a pod. Create the `envoy-initializer` ConfigMap:

```
kubectl apply -f configmaps/envoy-initializer.yaml
```

### Create the envoy-initializer Deployment

```
kubectl apply -f deployments/envoy-initializer.yaml
```
