# Initializing Pods

In this section you will create an [InitializerConfiguration](https://kubernetes.io/docs/admin/extensible-admission-controllers/#configure-initializers-on-the-fly) that forces new pods to be initialized by the Envoy Initializer.

### Create the envoy-initializer InitializerConfiguration

```
kubectl apply -f initializer-configurations/envoy.yaml
```

At this point new pods will be initialized by the `envoy-initializer`.
