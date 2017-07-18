# Initializing Deployments Based On Metadata

It's possible to select which objects are initialized using metadata. In this section the Envoy Initializer will be redeployed and configured to only initialize Deployments with an `initializer.kubernetes.io/envoy` annotation set to a non-empty value.

## Prerequisites

Delete the existing `helloworld` and `envoy-initializer` Deployments:

```
kubectl delete deployments helloworld envoy-initializer
```

## Deploy the Envoy Initializer

Deploy the Envoy Initializer with the `-require-annotation` flag set. This will ensure the Envoy proxy container is only injected into Deployments with an `initializer.kubernetes.io/envoy` annotation set to a non-empty value.

```
kubectl apply -f deployments/envoy-initializer-with-annotation.yaml
```

Create the `helloworld` Deployment:

```
kubectl apply -f deployments/helloworld.yaml 
```

Notice the `helloworld` Deployment has been initialized without injecting the Envoy proxy container:

```
kubectl get pods
```
```
NAME                                READY     STATUS    RESTARTS   AGE
envoy-initializer-460025406-f56d4   1/1       Running   0          56s
helloworld-3116035291-6nl6x         1/1       Running   0          10s
```

### Create the helloworld-with-annotation Deployment

```
kubectl apply -f deployments/helloworld-with-annotation.yaml
```

Notice the `helloworld-with-annotation` Deployment has been initialized with the Envoy proxy container:

```
kubectl get pods
```
```
NAME                                          READY     STATUS    RESTARTS   AGE
envoy-initializer-460025406-f56d4             1/1       Running   0          7m
helloworld-3116035291-6nl6x                   1/1       Running   0          6m
helloworld-with-annotation-3482720967-8b2qr   2/2       Running   0          6s
```
