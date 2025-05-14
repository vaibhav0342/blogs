---
title: "🚀 How to Install Essential DevOps Tools: Terraform, Ansible, Kubernetes, Git, Jenkins, Docker & More"
datePublished: Wed May 14 2025 06:32:33 GMT+0000 (Coordinated Universal Time)
cuid: cmankcza8000008i61jymd30u
slug: how-to-install-essential-devops-tools-terraform-ansible-kubernetes-git-jenkins-docker-and-more
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1747204273101/6dfaffa8-92d1-4fa7-98a0-2721ac7c720e.webp
tags: docker, aws, github, ansible, kubernetes, devops, jenkins

---

Whether you're just starting your journey into DevOps or setting up a new development environment, having the core tools installed and configured is the first step. This guide will walk you through installing the most commonly used DevOps tools on a **Linux (Ubuntu)** machine.

---

## 🧰 Prerequisites

* Ubuntu 20.04/22.04 LTS (recommended)
    
* Sudo privileges
    
* Basic command-line knowledge
    

---

## 1️⃣ Install Git

Git is a version control system used to track code changes.

```plaintext
bashCopyEditsudo apt update
sudo apt install git -y
git --version
```

---

## 2️⃣ Install Docker

Docker allows you to build and run containers.

```plaintext
bashCopyEditsudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce -y
sudo usermod -aG docker $USER
docker --version
```

> 🔄 Log out and back in for Docker group changes to take effect.

---

## 3️⃣ Install Ansible

Ansible is a powerful automation tool for configuration management.

```plaintext
bashCopyEditsudo apt update
sudo apt install ansible -y
ansible --version
```

---

## 4️⃣ Install Terraform

Terraform is an Infrastructure as Code (IaC) tool for provisioning cloud infrastructure.

```plaintext
bashCopyEditsudo apt update && sudo apt install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update
sudo apt install terraform -y
terraform -v
```

---

## 5️⃣ Install Jenkins

Jenkins is a widely-used open-source automation server.

```plaintext
bashCopyEditsudo apt update
sudo apt install openjdk-11-jdk -y

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Visit [`http://localhost:8080`](http://localhost:8080) to finish setup.

---

## 6️⃣ Install kubectl (Kubernetes CLI)

```plaintext
bashCopyEditcurl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```

---

## 7️⃣ Install Minikube (Local Kubernetes)

```plaintext
bashCopyEditcurl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
```

---

## ✅ Summary

You now have a powerful DevOps lab with the following tools installed:

* Git
    
* Docker
    
* Ansible
    
* Terraform
    
* Jenkins
    
* Kubernetes (via Minikube)
    
* kubectl