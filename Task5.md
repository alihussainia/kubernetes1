# Monitoring and Visualization

Let's first get the Helm.

```bash
 curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
```

Change the permissions

```bash
chmod 700 get_helm.sh
```

run the shell script

```bash
./get_helm.sh
```

### Adding Stable Repo

Let's add stable helm chart repo

```bash
helm repo add stable https://charts.helm.sh/stable
```

### Updating Repo

Let's update the repo

```bash
helm repo update
```

### Installing Prometheus

Let's install Prometheus, which will help us by scrapping metrics data from our cluster.

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

```bash
helm repo update
```

```bash
helm install prometheus prometheus-community/kube-prometheus-stack
```

```bash
kubectl get deployment

```

Now let's open Grafana dashboard

```bash
kubectl port-forward deploy/prometheus-grafana 3000
```

Visit browser and use this url:

```html
http://localhost:3000
        ```

Grafana Credentials:

```credentials
username = admin
password = prom-operator
```

### Minikube Docker Daemon

Let's use Minikube's docker daemon

```bash
eval $(minikube -p minikube docker-env)
```

### Container Check

```bash
docker ps
```

### Dashboard Check

```bash
minikube dashboard
```








