# `ValidatingAdmissionPolicy` demo

1. Create a k8s cluster on version `1.27.2` with Kind, enabling `ValidatingAdmissionPolicy` feature gate.
```shell
kind create cluster --config kind-config.yaml
```

2. Apply `ValidatingAdmissionPolicy` and `ValidatingAdmissionPolicyBinding`.
```shell
kubectl apply -f vap-replicas.yaml
kubectl apply -f vap-labels.yaml
```

3. Apply a `Deployment`.
```shell
kubectl apply -f deployment.yaml
```
