# Cleaning Up

The following commands will delete the Kubernetes objects associated with this tutorial.

```
kubectl delete initializerconfiguration envoy
```

```
kubectl delete deployment envoy-initializer helloworld helloworld-with-annotation
```

```
kubectl delete configmaps envoy envoy-initializer
```
