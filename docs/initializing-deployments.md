# Initializing Deployments

In this section you will create an [InitializerConfiguration](https://kubernetes.io/docs/admin/extensible-admission-controllers/#configure-initializers-on-the-fly) that force new Deployments to be initialized by the Envoy Initializer.

### Create the helloworld deployment

```
kubectl apply -f deployments/helloworld.yaml
```

Notice only one container is running in the `helloworld` Pod:

```
kubectl get pods
```
```
NAME                                 READY     STATUS    RESTARTS   AGE
envoy-initializer-3840443721-bjfb4   1/1       Running   0          20m
helloworld-3116035291-3sswk          1/1       Running   0          7s
```

### Create the Envoy Initializer InitializerConfiguration

```
kubectl apply -f initializer-configurations/envoy.yaml
```

At this point new Deployments will be initialized by the `envoy-initializer`.

#### Test the Envoy Initializer

Recreate the `helloworld` Deployment:

```
kubectl delete deployment helloworld
```

```
kubectl apply -f deployments/helloworld.yaml
```

Notice there are now two containers running in the `helloworld` Pod:

```
kubectl get pods
```
```
NAME                                 READY     STATUS    RESTARTS   AGE
envoy-initializer-3840443721-bjfb4   1/1       Running   0          22m
helloworld-3012526715-zk5kg          2/2       Running   0          31s
```

The second container is the Envoy proxy which was injected into the Pod by the Envoy Initializer.
