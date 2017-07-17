# Deploy the Envoy Initializer

The Envoy Initializer is a [Kubernetes initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects the [envoy](https://lyft.github.io/envoy) proxy into a pod based on policy.

## Install

The envoy proxy requires a [configuration file](https://lyft.github.io/envoy/docs/configuration/configuration.html) before it canbe used to forward trafic to other containers in a pod. Store the default `envoy.json` configuration in a configmap:

```
kubectl create configmap envoy --from-file envoy.json
```

The `envoy-initializer` is configured using a configmap, identified by the `-configmap` flag, which provides the containers and volumes to inject into a pod. Create the `envoy-initializer` configmap:

```
kubectl apply -f configmaps/envoy-initializer.yaml
```

```
kubectl apply -f initializer-configurations/envoy.yaml 
```

```
kubectl apply -f deployments/envoy-initializer.yaml
```
