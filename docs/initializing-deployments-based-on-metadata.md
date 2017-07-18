# Initializing Deployments Based On Metadata

It's possible to select which objects are initialized using metadata such as annotations. This lab walks you through initializing uninitialized Deployments with the `initializer.kubernetes.io/envoy` annotation set to a non-empty value.

## Prerequisites

Delete the existing `helloworld` and `envoy-initializer` deployments:

```
kubectl delete deployments helloworld envoy-initializer
```

## Deploy the Envoy Initializer

The following command will redeploy the Envoy Initializer with the `-require-annotation` flag set to `true`, which will ensure the envoy proxy container is only injected into Deployments with the `initializer.kubernetes.io/envoy` annotation set to a non-empty value.

```
kubectl apply -f deployments/envoy-initializer-with-annotation.yaml
```

Create the `helloworld` deployment:

```
kubectl apply -f deployments/helloworld.yaml 
```

Notice the `helloworld` deployment has been initialized without injecting the envoy proxy container:

```
kubectl get pods
```
```
NAME                                READY     STATUS    RESTARTS   AGE
envoy-initializer-460025406-f56d4   1/1       Running   0          56s
helloworld-3116035291-6nl6x         1/1       Running   0          10s
```

### Create the helloworld-with-annotation deployment

Create the `helloworld-with-annotation` deployment:

```
kubectl apply -f deployments/helloworld-with-annotation.yaml
```

Notice the `helloworld-with-annotation` deployment has been initialized with the envoy proxy container:

```
kubectl get pods
```
```
NAME                                          READY     STATUS    RESTARTS   AGE
envoy-initializer-460025406-f56d4             1/1       Running   0          7m
helloworld-3116035291-6nl6x                   1/1       Running   0          6m
helloworld-with-annotation-3482720967-8b2qr   2/2       Running   0          6s
```
