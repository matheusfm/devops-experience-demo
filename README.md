# Marvin and `ValidatingAdmissionPolicy` demo

This repository contains the commands and examples used in our talk at [DevOps Experience](https://www.youtube.com/@devopsheroes).

## Creating a k8s cluster with [Kind](https://kind.sigs.k8s.io/)

The command below creates a k8s cluster on version `1.27.2` with [Kind](https://kind.sigs.k8s.io/).

```shell
kind create cluster --config kind-config.yaml
```

The [`kind-config.yaml`](./kind-config.yaml) configuration file enables the feature gate `ValidatingAdmissionPolicy`.


## Creating `ValidatingAdmissionPolicy`

The following commands creates validating admission policies and their bindings.

```shell
kubectl apply -f vap/replicas.yaml
kubectl apply -f vap/labels.yaml
```

See the [k8s official documentation](https://kubernetes.io/docs/reference/access-authn-authz/validating-admission-policy) for more details.

## Playing with deployments

The file [`deployment.yaml`](./deployment.yaml) is an example of a k8s `Deployment` and you can use it for tests.

Edit the file for your tests, such as increasing replicas and adding labels.

```shell
kubectl apply -f deployment.yaml
```

## Scanning the cluster with [Marvin](https://github.com/undistro/marvin)

Since you have Marvin installed, you can scan a cluster by the following command.

```shell
marvin scan -f checks/ --disable-builtin
```

This command uses the custom checks from the [`checks/`](./checks) directory.

Visit the [Marvin](https://github.com/undistro/marvin) repository for in-depth information.
