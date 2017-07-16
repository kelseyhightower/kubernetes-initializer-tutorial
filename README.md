# Kubernetes Initializer Tutorial

## Usage

Create a Kubernetes 1.7.0+ clusters with the alpha API enabled:

```
gcloud alpha container clusters create k0 \
  --enable-kubernetes-alpha \
  --cluster-version 1.7.0
```

Store the envoy config in a configmap:

```
kubectl create configmap envoy --from-file envoy.json
```

### Deploy the Envoy Initializer

Store the Envoy Initializer configuration in a configmap:

```
kubectl apply -f configmaps/envoy-initializer.yaml
```

Create the envoy initializer configuration:

```
kubectl apply -f initializer-configurations/envoy.yaml 
```

Create the `envoy-initializer` deployment:

```
kubectl apply -f deployments/envoy-initializer.yaml
```
