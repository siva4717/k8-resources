````markdown
# Kubernetes Workstation Setup & Core Concepts

## 🚀 Workstation Setup
This guide helps you set up a Kubernetes-ready workstation with Docker, kubectl, eksctl, and AWS CLI.

---

## 🐳 1. Install Docker
Install Docker Desktop for running containers locally.

**Docs:** https://docs.docker.com/get-docker/

---

## ☸️ 2. Install kubectl
Command-line tool for Kubernetes clusters.

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/latest/2023-05-23/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
````

---

## 🔧 3. Install eksctl

Used to create and manage EKS clusters.

```bash
curl --location "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz
sudo mv eksctl /usr/local/bin
```

---

## 🔐 4. AWS CLI Configure

```bash
aws configure
```

Provide:

* Access Key
* Secret Key
* Region (example: ap-south-1)
* Output (json)

---

## ☸️ 5. Create EKS Cluster

```bash
eksctl create cluster --config-file=eks.yaml
```

---

## 🗑️ 6. Delete EKS Cluster

```bash
eksctl delete cluster --config-file=eks.yaml
```

---

# Kubernetes Concepts

## 📦 Namespace

A virtual cluster inside Kubernetes used to organize and isolate resources.

---

## 🧱 Pod

Smallest deployable unit in Kubernetes.

### Pod Components:

* **env** → Environment variables
* **labels** → Key-value identifiers used by services & selectors
* **annotations** → Metadata for tools (non-identifying)
* **configMap** → Store non-sensitive configuration
* **secret** → Store sensitive data (base64 encoded)
* **resources** → CPU & memory limits/requests

---

# 🌐 Services

Services expose Pods and provide networking.

### 1. **ClusterIP** (default)

* Used for **internal** communication
* Pod-to-Pod communication
* Load balancing inside the cluster
* Service name acts as DNS

### 2. **NodePort / LoadBalancer**

* Expose the application to the **outside world**

### How Pods connect to Services:

➡️ **Services use labels as selectors** to find Pods

---

# 📊 ReplicaSet

Ensures a specified number of pod replicas are running.

---

# 🚀 Deployment

Manages:

* ReplicaSets
* Rolling updates (default)
* Rollbacks

### Relationship:

```
pod < replicaset < deployment
```

Deployment creates ReplicaSet → ReplicaSet creates Pods.

---

### ✅ End of README.md

```
```
