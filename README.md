# 🖥 Minikube Installation on Ubuntu 22.04

This repository provides a **step-by-step guide** to install and set up **kubectl** and **Minikube** on Ubuntu 22.04, including running Minikube on AWS EC2.

---

## 🔗 Useful Links

- **Install and Set Up kubectl on Linux**  
  Link: [https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

- **Minikube Set Up**  
  Link: [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)

---

## 📌 What is Minikube?

Minikube is a **lightweight Kubernetes (K8s) setup** that can create a **Virtual Machine (VM)** on your local machine or in a cloud instance.  
It deploys a **simple single-node cluster**, ideal for development and testing purposes.

---

## 🛠 Prerequisites

- Ubuntu 22.04 LTS
- Sudo privileges
- AWS EC2 instance (optional for cloud setup)
- Docker installed

---

## Step 1: Create an AWS EC2 Instance with Ubuntu 22

- **Operating System:** Ubuntu 22.04  
- **Instance Size:** t2.medium or t2.large  
- **CPU & Storage:** 2 CPUs, 32 GB Storage  

---

## Step 2: Install Docker

```bash
sudo apt-get update
sudo apt-get install -y docker.io
sudo systemctl enable docker
sudo systemctl start docker
docker --version

# Optional: Manage Docker as non-root user
sudo usermod -aG docker $USER
newgrp docker
````

---

## Step 3: Install kubectl

Follow official documentation: [Install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg

curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.32/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg

echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.32/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo chmod 644 /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubectl

kubectl version --client
```

---

## Step 4: Install Minikube

Official documentation: [Minikube Setup](https://minikube.sigs.k8s.io/docs/start/)

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

---

## Step 5: Start Minikube

```bash
minikube start --force
minikube status
```

* This initializes a **single-node Kubernetes cluster** on your local machine or cloud instance.

---

## ✅ References

* [Kubernetes Official Documentation](https://kubernetes.io/docs/home/)
* [Minikube Official Documentation](https://minikube.sigs.k8s.io/docs/)

```


