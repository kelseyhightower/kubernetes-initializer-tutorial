# Deploy The Envoy Initializer

The Envoy Initializer is a [Kubernetes Initializer](https://kubernetes.io/docs/admin/extensible-admission-controllers/#what-are-initializers) that injects an [Envoy](https://lyft.github.io/envoy) proxy into Deployments based on containers and volumes defined in a [ConfigMap](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap).

## Install

### Store the Envoy configuration in a ConfigMap

Envoy requires a [configuration file](https://lyft.github.io/envoy/docs/configuration/configuration.html) before it can proxy traffic to other containers in a Pod. Store the `envoy.json` configuration file in a ConfigMap:

```
kubectl create configmap envoy --from-file envoy.json
```

### Create the Envoy Initializer ConfigMap 

The Envoy Initializer is configured using a ConfigMap, identified by the `-configmap` flag, which provides the containers and volumes to inject into a Deployment. Create the `envoy-initializer` ConfigMap:

```
kubectl apply -f configmaps/envoy-initializer.yaml
```

### Create the Envoy Initializer Deployment

Deploy the `envoy-initializer` controller:

```
kubectl apply -f deployments/envoy-initializer.yaml
```

The `envoy-initializer` Deployment sets pending initializers to an empty list which bypasses initialization. This prevents the Envoy Initializer from getting stuck waiting for initialization, which can happen if the `envoy` [Initialization Configuration](initializing-deployments.md#create-the-envoy-initializer-InitializerConfiguration) is created before the `envoy-initializer` Deployment.

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  initializers:
    pending: []
```

At this point the Envoy Initializer is ready to initialize new Deployments.
