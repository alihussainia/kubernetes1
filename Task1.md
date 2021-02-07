# Task1 - Installing the Pre-requisites

---

In this task we will install the pre-requisite tools for completing our project.

---


## Tools

The tools we will install are:

| Tool      | Description               |
|:----------|:--------------------------|
| [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) | The Kubernetes CLI. |
| [docker](https://docs.docker.com/engine/install/ubuntu/) | The container runtime used by `minikube`.|
| [Minikube](https://github.com/kubernetes/minikube) | A single-node Kubernetes cluster inside a contianer. |
| [Helm](https://helm.sh) | The Kubernetes package manager. |
| [kubectx and kubens](https://github.com/ahmetb/kubectx) | Helper scripts for changing Kubernetes contexts and namespaces. |
| [kubetail](https://github.com/johanhaleby/kubetail) | Helper script to easily tail logs from Pods. |

**Notes**

* `kubectx`, `kubens` and `kubetail` only work on Mac or Linux systems.

### Kubectl Installation

The Kubernetes Command-Line tool that allows to run commands against Kubernetes clusters. The instructions for installing `kubectl` can be found [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/).  

There are various ways to install `kubectl` but we will focus on how to do it using `curl`.  Scroll down the page until you reach the section _Install kubectl binary via curl_.  We will install the latest version of `kubectl`, so use the following commands.

```bash
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl
```


Now, let's change the file permission for kubectl

```bash
chmod +x ./kubectl
```


Let's move it to the /usr/local/bin directory

```bash
sudo mv ./kubectl /usr/local/bin/kubectl
```


### Docker Installation

Update the apt package index and install packages to allow apt to use a repository over HTTPS. Copu and Paste these **commands **one by one in the terminal. The official installation documentation page for docker can be found [here](https://docs.docker.com/engine/install/ubuntu/).

```bash
sudo apt-get update
```

Then this cmd:

```bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

```

Press **Y** and then Enter.

Then we have to add Docker’s official GPG key:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```

Use the following command to set up the stable repository:

```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

```

Press **Y** and then Enter.

And install the latest version of Docker Engine and containerd
```

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io

```

##### Allowing Permission to the sock:

```bash
sudo chmod 666 /var/run/docker.sock
```

### Minikube Installation

Installing minikube using binary download option.

The releases for `minikube` can be found [here](https://github.com/kubernetes/minikube/releases).

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### Snap Installation

Snap is a software deployment and package management system developed by Canonical.

```bash
sudo apt install snap

```

### Helm Installation

Helm is a package manager for Kubernetes.
```

```bash
sudo snap install helm --classic

```

### Kubectx and Kubens Installation

Helper scripts for changing Kubernetes contexts and namespaces. The github repo for `kubectx` and `kubens` can be found [here](https://github.com/ahmetb/kubectx). First Let's get Kubectx and Kubens from github using:

```bash
wget https://raw.githubusercontent.com/ahmetb/kubectx/master/kubectx

```

And then

```bash
wget https://raw.githubusercontent.com/ahmetb/kubectx/master/kubens

```

Now, let's change the file permission for kubectx and kubens

```bash
sudo chmod +x kubectx kubens

```

Let's move it to the /usr/local/bin directory

```bash
sudo mv kubectx kubens /usr/local/bin

```

### Kubetail Installation

A helper script for easily tail logs from pods.

```bash
wget https://raw.githubusercontent.com/johanhaleby/kubetail/master/kubetail

```

Now, let's change the file permission for kubetail

```bash
sudo chmod +x kubetail

```

Let's move it to the /usr/local/bin directory

```bash
sudo mv kubetail /usr/local/bin
```
