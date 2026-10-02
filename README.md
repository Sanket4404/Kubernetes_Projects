# Kubernetes Projects

A hands-on collection of Kubernetes projects covering **Deployments, Services, ConfigMaps, MongoDB, persistent storage, Jobs, CronJobs, DaemonSets, and multi-container applications**.

This repository focuses on practical Kubernetes learning through manifests, deployments, troubleshooting, and application/database connectivity.

## 🎯 What This Repository Covers

* Kubernetes Pods
* Deployments
* Replica management
* Services
* LoadBalancer services
* ConfigMaps
* MongoDB
* Node.js applications
* Multi-container Pods
* Persistent Volumes
* Jobs
* CronJobs
* DaemonSets
* Container images from Docker Hub
* Application/database connectivity

## 📁 Repository Structure

```text
Kubernetes_Projects/
├── apache/
├── db-demo-app/
├── express-demo/
├── testkubeapp/
├── cron-job.yml
├── deamonsets.yml
├── deployment-node-app.yml
├── host-pv.yml
├── jobs.yml
├── mongo-config.yml
├── mongo-db.yml
├── node-app.yml
├── service-node-app.yml
└── README.md
```

## 🏗️ Example Application Architecture

```text
                 Kubernetes Cluster
                        │
              ┌─────────▼─────────┐
              │    Node.js App    │
              │    Deployment     │
              └─────────┬─────────┘
                        │
                        │ MongoDB
                        ▼
                 ┌─────────────┐
                 │   MongoDB   │
                 │   Database  │
                 └─────────────┘
                        ▲
                        │
                  ConfigMap
```

## 🐳 Docker Images

The manifests demonstrate deploying images hosted on Docker Hub.

Example:

```yaml
containers:
  - name: nodedb-app
    image: sds04/db-demo-app:02
```

## 🚀 Deploy Applications

Start with a running Kubernetes cluster.

Apply a Deployment:

```bash
kubectl apply -f deployment-node-app.yml
```

Check deployments:

```bash
kubectl get deployments
```

Check Pods:

```bash
kubectl get pods
```

Check Services:

```bash
kubectl get svc
```

## ⚙️ ConfigMaps

The project demonstrates using ConfigMaps for application configuration.

Example:

```yaml
env:
  - name: MONGO_HOST
    valueFrom:
      configMapKeyRef:
        name: mongo-congfig
        key: MONGO_HOST

  - name: MONGO_PORT
    valueFrom:
      configMapKeyRef:
        name: mongo-congfig
        key: MONGO_PORT
```

This separates configuration from application container images.

## 💾 Persistent Storage

The repository contains persistent-storage practice using:

* PersistentVolumes
* Host-based storage
* Database persistence concepts

The `host-pv.yml` manifest demonstrates how Kubernetes storage can be connected to workloads.

## ⏱️ Jobs and CronJobs

Jobs are used for tasks that should run to completion.

CronJobs are used for scheduled tasks.

```bash
kubectl get jobs
kubectl get cronjobs
```

## 🔄 DaemonSets

The repository includes a DaemonSet example for understanding workloads that are scheduled according to node-level DaemonSet behavior.

```bash
kubectl get daemonsets
```

## 🧠 Kubernetes Concepts

| Concept          | Purpose                             |
| ---------------- | ----------------------------------- |
| Pod              | Smallest Kubernetes workload        |
| Deployment       | Manage replicated Pods              |
| Replica          | Run multiple application instances  |
| Service          | Provide network access to workloads |
| ConfigMap        | Store non-sensitive configuration   |
| MongoDB          | Database workload                   |
| PersistentVolume | Persistent storage                  |
| Job              | One-time task                       |
| CronJob          | Scheduled task                      |
| DaemonSet        | Node-oriented workload              |
| LoadBalancer     | External service exposure           |

## 🔍 Troubleshooting

Useful commands:

```bash
kubectl get pods -o wide
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl describe deployment <deployment-name>
kubectl describe service <service-name>
```

For a failing Pod:

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## 🧪 Learning Approach

The repository builds Kubernetes understanding step by step:

```text
Container
   ↓
Pod
   ↓
Deployment
   ↓
Service
   ↓
Configuration
   ↓
Storage
   ↓
Jobs / CronJobs
   ↓
Node-level workloads
```

These fundamentals are also used in my larger AWS EKS DevOps project.

## 👨‍💻 Author

**Sanket Shinde**

GitHub: https://github.com/Sanket4404
