# Best Practices

The following list represents a set of best practices to follow when building Initializers.


* Initializers must have a unique fully qualified name. Examples:

```
initializer.vaultproject.io
envoy.initializer.example.com
```
 
* Initializers should be deployed using a Deployment for easy upgrades and auto restarts.
* Initializers should explicitly set the list of pending initializers to exclude itself, or to an empty array, to avoid getting stuck waiting to initialized. Examples:

Set the list of pending initializers to exclude itself

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  initializers:
    pending:
      - initializer.vaultproject.io
```

Set the pending initializers to an empty array:

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  initializers:
    pending: []
```

* 
