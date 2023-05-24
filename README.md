# Marvin and `ValidatingAdmissionPolicy` demo

#### Create a k8s cluster on version `1.27.2` with Kind, enabling `ValidatingAdmissionPolicy` feature gate.
```shell
kind create cluster --config kind-config.yaml
```

#### Apply `ValidatingAdmissionPolicy` and `ValidatingAdmissionPolicyBinding`.
```shell
kubectl apply -f vap/replicas.yaml
kubectl apply -f vap/labels.yaml
```

#### Try to apply a `Deployment`.
```shell
kubectl apply -f deployment.yaml
```

#### Scan the cluster with marvin
```shell
marvin scan -f checks/ --disable-builtin
```
