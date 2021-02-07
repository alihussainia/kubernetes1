 # Task4: Deploying an Application

Change directory to the Project folder present on the Desktop

```bash
cd /home/rhyme/Desktop/Project
```

Clone the application repository from Github

```bash
git clone "https://github.com/alihussainia/Deploying-Web-Apps-on-a-Kubernetes-Single-Node-Cluster-using-Minikube.git"
```

Change the name of the app directory to simple_app

```bash
mv Deploying-Web-Apps-on-a-Kubernetes-Single-Node-Cluster-using-Minikube simple_app
```

Then move into the app folder using:

```bash
cd simple_app
```

### Application Structure

In this github [repository](https://github.com/alihussainia/Deploying-Web-Apps-on-a-Kubernetes-Single-Node-Cluster-using-Minikube) there are files for a simple application  needed to build a _Docker_ image and run it on _Kubernetes_.

**NOTE: Below is just the tree not code so don't run it on terminal**

```python3
- Repository
  - html/
      - index.html     
  - kubernetes/        
      - deployment.yaml
      - service.yaml 
  - Dockerfile 
      
```

### Dockerfile

By looking at the `Dockerfile` we will see that it is very basic.  Using an _Alpine_ version of _Nginx_ to serve a single page of static content.

**NOTE: Below is just the content not code so don't run it on terminal**


```dockerfile
FROM nginx:1.15.0-alpine
COPY html/ /usr/share/nginx/html/
```

### Docker Image

Let's first build the docker image using the docker daemon provided by the minikube

If you are starting out again after a break

```bash
minikube start
```

And then this command:

```bash
eval $(minikube docker-env)
```

The whole CMD should be used including the "."

```bash
docker build -t simple-app:v1 .
```

Let's test the image, first by running the container

```bash
docker run -d -p 8000:80 simple-app:v1
```

Then calling the minikube ip address with port 8000

```bash
curl `minikube ip`:8000
```

### _Kubernetes_ manifests

The `deployment.yaml` manifest describes to _Kubernetes_ how to run the _Docker_ container inside a _Pod_.

**NOTE: This is just the content not code, so don't run it on terminal**

```yaml
apiVersion: apps/v1 
kind: Deployment
metadata:
  name: simple-app
spec:
  selector:
    matchLabels:
      app: simple-app
  replicas: 2
  template:
    metadata:
      labels:
        app: simple-app
    spec:
      containers:
      - name: simple-app
        image: simple-app:v1
        ports:
        - containerPort: 80
```

The `service.yaml` manifest describes to _Kubernetes_ how to make the _Pods_ available on the network by using a _Service_ resource type

```yaml
kind: Service
apiVersion: v1
metadata:
  name: simple-app
spec:
  selector:
    app: simple-app
  type: NodePort
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

### Deployment

lets deploy our application to _Minikube_.

```bash
kubectl -n default create -f kubernetes
```

### Pod Check

```bash
kubectl -n default get pod
```

We can see that we have 2 _Pods_ running.  This is because we asked for 2 `replicas` inside the `deployment.yaml`.

### Service Check

```bash
kubectl -n default get service
```

_NodePort_ makes the mapped container port directly available on the _Kubernetes_ node.

### Access Test

let's test that we can access the application running inside _Minikube_

```bash
curl `minikube service -n default simple-app --url`
```

### Dashboard

Make sure that you are looking at the `default` namespace and then click on _Deployments_.

```bash
minikube dashboard
```
