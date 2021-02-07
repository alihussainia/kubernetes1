# Creating a Cluster with Minikube

### Minikube Options

A cluster can be created with just `minikube start` but we want to customise the configuration a bit.  So let's have a look at the possible options.

```bash
minikube start -h
```

### Starting a Cluster

For our first cluster we want to use Kubernetes version `v1.20.0` and give it 2 cpus with 4GB memory. 

```bash
minikube start --cpus 2 --memory 4096 --kubernetes-version v1.20.0 
```

This is the latest Kubernetes version available at the moment [link](https://kubernetes.io/docs/setup/release/notes/)

### Status Check

Once our cluster is created we want to check on its status.

```bash
minikube status
```

### Minikube Addons 

Lets see what Add-Ons are available.

```bash
minikube addons list
```

Let's enable few more addons using:

```bash
minikube addons enable ingress
minikube addons enable registry
minikube addons enable metrics-server
minikube addons enable dashboard
```

### Dashboard

We can then access the _Dashboard_ using:

```bash
minikube dashboard
```

### Services

We can also see what services are available in the cluster using:

```bash
minikube service list
```

### Minikube logs

If we want to see the _Minikube_ logs we can also do that using

```bash
minikube logs
```

### Minikube Docker Daemon

To point the terminal to use the docker daemon inside minikube use this:

```bash
 eval $(minikube docker-env)
 ```

This will show uscontainers inside the minikube:

```bash
docker ps
```
