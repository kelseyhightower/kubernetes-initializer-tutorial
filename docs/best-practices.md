# Best Practices

The following list represents a set of best practices to follow when building Initializers.


* Initializers must have a unique fully qualified name. Examples:

```
initializer.vaultproject.io
envoy.initializer.example.com
```
 
* Initializers should be deployed using a Deployment for easy upgrades and auto restarts.
* Initializers should explicitly set the list of pending initializers to exclude itself, or to an empty array, to avoid getting stuck waiting to initialize. Examples:

Set the list of pending initializers to exclude itself

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  initializers:
    pending:
      - initializer.vaultproject.io
      # Do not include the Envoy Initializer
      # - envoy.initializer.kubernetes.io
  name: envoy-initializer
```

Set the pending initializers to an empty array:

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  initializers:
    pending: []
```

* Limit the scope of objects to be initialized to the smallest subset possible using an InitializerConfiguration. Examples:

Limit the `envoy.initializer.kubernetes.io` Initializer to Deployment objects:

```
apiVersion: admissionregistration.k8s.io/v1alpha1
kind: InitializerConfiguration
metadata:
  name: envoy
initializers:
  - name: envoy.initializer.kubernetes.io
    rules:
      - apiGroups:
          - "*"
        apiVersions:
          - "*"
        resources:
          - deployments
```

* Use annotations to enable opting in or out of initialization. Examples:

Opting in using an annotation:

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  annotations:
    "initializer.kubernetes.io/envoy": "true"
  labels:
    app: helloworld
    envoy: "true"
  name: helloworld-with-annotation
...
```
The complete [helloworld-with-annotation deployment](https://raw.githubusercontent.com/kelseyhightower/kubernetes-initializer-tutorial/master/deployments/helloworld-with-annotation.yaml).

Use a flag on the Initializer to enable or disable an annotation to trigger initialization. See the [Envoy Initializer](https://github.com/kelseyhightower/kubernetes-initializer-tutorial/tree/master/envoy-initializer) for a complete example.
