

# CKA 2024 Preparation - Darshan Vasani

This repository serves as a comprehensive resource for the Certified Kubernetes Administrator (CKA) 2024 exam preparation, following along with the excellent YouTube series by **Tech Tutorials with Piyush**. It contains detailed notes, YAML configurations, code snippets, and hands-on exercises to solidify your understanding of core Kubernetes concepts.

**Repository Author:** Darshan Vasani

-----

## 🎯 About This Repository

This repository aims to:

  * **Provide structured notes:** Detailed explanations of key CKA topics covered in the YouTube series.
  * **Host practical YAML files:** Ready-to-use Kubernetes manifests for various resources, enabling hands-on practice.
  * **Include code snippets:** Relevant commands and scripts for common Kubernetes operations.
  * **Support active learning:** By following along and practicing the examples, you can build a strong foundation in Kubernetes administration.

-----

## 📺 YouTube Series: Tech Tutorials with Piyush - CKA 2024

This repository is built as a companion to the **CKA 2024 series by "Tech Tutorials with Piyush"** on YouTube. Piyush provides clear, concise, and highly effective explanations for all the CKA topics.

I highly recommend subscribing to his channel and following along with his videos for the best learning experience.
 

-----

## 📂 Repository Structure

The repository is organized by "Day" or "Video Number" to align with the structure of the YouTube series. Each folder will contain the relevant notes, YAML files, and code for that specific video.

```
.
├── Day01_Introduction/
│   └── notes.md
├── Day02_Kubernetes_Architecture/
│   └── notes.md
├── Day03_Kubectl_Basics/
│   └── notes.md
├── Day04_Pods/
│   ├── notes.md
│   └── pod-example.yaml
├── Day08_Deployments_ReplicaSets/
│   ├── notes.md
│   ├── rc.yaml
│   ├── deploy.yaml
│   └── diagrams.md (or directly in notes.md if preferred)
└── ... (more days/videos will be added)
```

-----

## 📝 Notes & Explanations

Each topic will have a `notes.md` file within its respective `Day` folder. These notes include:

  * **Key Concepts:** Core definitions and principles.
  * **Detailed Explanations:** In-depth breakdown of how Kubernetes resources work.
  * **Flow Diagrams:** Visual representations of processes (e.g., Rolling Updates).
  * **Command Line Examples:** `kubectl` commands with explanations.
  * **YAML Manifest Breakdowns:** Explanations of each field in the YAML files.

### Example: Day 08 - Deployments and Replica Sets

#### **Key Concepts**

  * **Pod (📦):** Smallest deployable unit, single application instance.
  * **Replication Controller (RC) / Replica Set (RS) (🛡️):** Ensures a desired number of identical Pods are running, providing auto-healing and high availability.
  * **Deployment (🚀):** Higher-level object managing Replica Sets, enabling declarative updates, rolling updates, and easy rollbacks.

#### **YAML File Examples**

**`rc.yaml` (ReplicaSet)**

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
  labels:
    env: demo
spec:
  replicas: 3
  selector:
    matchLabels:
      env: demo
  template:
    metadata:
      labels:
        app: nginx
        env: demo
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

**`deploy.yaml` (Deployment)**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deploy
  labels:
    env: demo
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

#### **`kubectl` Commands**

```bash
# Get all running pods
kubectl get pods

# Get replica sets
kubectl get rs

# Get deployments
kubectl get deploy

# Apply a YAML file
kubectl apply -f rc.yaml
kubectl apply -f deploy.yaml

# Delete a resource
kubectl delete rs nginx-rs
kubectl delete deploy nginx-deploy

# Scale a ReplicaSet imperatively
kubectl scale --replicas=5 rs/nginx-rs

# Scale a Deployment imperatively
kubectl scale --replicas=10 deploy/nginx-deploy

# Edit a live object (e.g., Deployment)
kubectl edit deploy nginx-deploy

# Update image of a Deployment (rolling update)
kubectl set image deployment/nginx-deploy nginx=nginx:1.9.1

# Check rollout history of a Deployment
kubectl rollout history deployment/nginx-deploy

# Undo the last rollout
kubectl rollout undo deployment/nginx-deploy

# Generate YAML from an imperative command (dry run)
kubectl create deployment my-new-app --image=my-image --dry-run=client -o yaml > my-new-app.yaml
```

-----

## ✨ Getting Started

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/DarshanVasani/cka-2024-notes.git
    cd cka-2024-notes
    ```
2.  **Follow the YouTube series:** Watch the "Tech Tutorials with Piyush" CKA 2024 playlist.
3.  **Explore the corresponding `DayXX` folders:** Review the `notes.md`, `yaml` files, and practice the commands in your Kubernetes cluster (Minikube, Kind, or a cloud-based cluster).

-----

## 🤝 Contribution

This repository is maintained by Darshan Vasani. If you find any errors, have suggestions for improvements, or would like to contribute, feel free to open an issue or submit a pull request. Your contributions are highly appreciated\!

-----


**Happy Learning and Good Luck with your CKA Exam\!** 🎉