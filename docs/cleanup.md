# Cleaning Up

The following commands will delete all the Kubernetes objects associated with this tutorial.

```
kubectl delete initializerconfiguration envoy
```

```
kubectl delete deployment envoy-initializer helloworld
```

```
kubectl delete configmaps envoy envoy-initializer
```
