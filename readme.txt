Here are the steps in 5 lines:

1️⃣ Open hosts file: C:\Windows\System32\drivers\etc\hosts (as Administrator).
2️⃣ Add this line at the bottom: 192.168.49.2 nginx.local.
3️⃣ Save the file and close it.
4️⃣ Run ipconfig /flushdns in CMD/PowerShell.
5️⃣ Test using ping nginx.local or open http://nginx.local in the browser.



minikube-learnings/
│
├── README.md
├── .gitignore
│
├── docker/
│   ├── Dockerfile
│   └── index.html
│
├── deployments/
│   └── nginx-deployment.yaml
│
├── services/
│   ├── nginx-clusterip.yaml
│   ├── nginx-nodeport.yaml
│   └── nginx-lb.yaml
│
├── pods/
│   └── multi-container-pod.yaml
│
└── ingress/
    └── nginx-ingress.yaml


    # Kubernetes Minikube Practice

This repository contains hands-on practice with Kubernetes using Minikube.

The project demonstrates core Kubernetes concepts such as:

- Pods
- Deployments
- Services (ClusterIP, NodePort, LoadBalancer)
- Multi-container Pods
- Ingress
- Docker containerization

---

# Repository Structure

```
minikube-learnings/
│
├── docker/
│   ├── Dockerfile
│   └── index.html
│
├── deployments/
│   └── nginx-deployment.yaml
│
├── services/
│   ├── nginx-clusterip.yaml
│   ├── nginx-nodeport.yaml
│   └── nginx-lb.yaml
│
├── pods/
│   └── multi-container-pod.yaml
│
└── ingress/
    └── nginx-ingress.yaml
```

---

# Prerequisites

Install the following tools:

- Docker
- Minikube
- kubectl
- Git

---

# Start Minikube

```
minikube start
```

Verify cluster:

```
kubectl get nodes
```

---

# Build Docker Image

Inside project directory:

```
minikube image build -t nginx-hello .
```

---

# Deploy Application

Deploy nginx deployment:

```
kubectl apply -f deployments/nginx-deployment.yaml
```

Verify pods:

```
kubectl get pods
```

---

# Create Services

ClusterIP service:

```
kubectl apply -f services/nginx-clusterip.yaml
```

NodePort service:

```
kubectl apply -f services/nginx-nodeport.yaml
```

LoadBalancer service:

```
kubectl apply -f services/nginx-lb.yaml
```

---

# Access LoadBalancer

Run:

```
minikube tunnel
```

Check services:

```
kubectl get svc
```

Open the external IP in browser.

---

# Multi-container Pod Demo

```
kubectl apply -f pods/multi-container-pod.yaml
```

Check logs:

```
kubectl logs multi-container-pod -c sidecar-container
```

---

# Ingress Setup

Enable ingress in Minikube:

```
minikube addons enable ingress
```

Deploy ingress:

```
kubectl apply -f ingress/nginx-ingress.yaml
```

---

# Clean Up

Delete resources:

```
kubectl delete -f deployments/
kubectl delete -f services/
kubectl delete -f pods/
kubectl delete -f ingress/
```

Stop Minikube:

```
minikube stop
```

---

# Author

Gokulraj R  
