# Task3 - Exploring Cluster

## Dashboard

Let's explore our dashboard in more detail.

```bash
minikube dashboard
```

## Kubectl

We installed Kubectl in the first task, now let's explore it.

### Kubernetes server and client Version

```bash
kubectl version
```

### Available Nodes

```bash
kubectl get node
```

### Node Details 

```bash
kubectl describe node minikube
```

### Available Namespace

```bash
kubectl get namespace
```

### Available Pods 

```bash
kubectl -n kube-system get pod
```

### Pod's YAML definition 

```bash
kubectl -n kube-system get po kube-apiserver-minikube -o yaml
```

### Services Display

```bash
kubectl -n kube-system get services
```
