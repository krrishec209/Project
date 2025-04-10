2) 5 Real-Time Kubernetes Interview Questions & Answers

1️⃣ How does Kubernetes handle multi-tenancy, and what are the best practices?

Answer:
Multi-tenancy in Kubernetes allows multiple teams or applications to share a cluster securely. There are three approaches:

1. Soft Multi-Tenancy: Uses Namespaces, Resource Quotas, and RBAC to isolate workloads.

2. Hard Multi-Tenancy: Implements separate clusters per tenant using Cluster API or Virtual Clusters (vCluster).

3. Network Isolation: Uses Network Policies to restrict cross-namespace communication.


✅ Best Practices:

Enforce RBAC (Role-Based Access Control).

Use Pod Security Policies (PSPs) or OPA/Gatekeeper for compliance.

Implement resource quotas & limits to prevent noisy neighbor issues.


2️⃣ How does Kubernetes implement rolling back a failed deployment?

Answer:
Kubernetes supports automated rollbacks via the kubectl rollout undo command.

✅ Steps to rollback:

1. Identify the faulty deployment:

kubectl rollout history deployment my-app

2. Rollback to the last successful version:

kubectl rollout undo deployment my-app


3. If needed, rollback to a specific revision:

kubectl rollout undo deployment my-app --to-revision=2


3️⃣ How does Kubernetes handle persistent storage across pod restarts?

Answer:
Kubernetes uses PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs) to provide stable storage that survives pod restarts.

✅ Key Storage Options:

EBS (AWS), Azure Disk, GCE Persistent Disk → Single-node persistent storage.

NFS, Ceph, GlusterFS → Shared storage across multiple pods.

CSI (Container Storage Interface) → Standardized API for dynamic volume provisioning.


👉 Example YAML for PVC:

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
 name: my-pvc
spec:
 accessModes:
 - ReadWriteOnce
 resources:
 requests:
 storage: 10Gi


4️⃣ What are the main differences between Horizontal Pod Autoscaler (HPA) and Cluster Autoscaler?

Answer:

✅ Example: Enabling HPA for CPU-based scaling

kubectl autoscale deployment my-app --cpu-percent=50 --min=2 --max=10

👉 Best Practice: Use VPA (Vertical Pod Autoscaler) for optimizing pod resource allocation alongside HPA.


5️⃣ How do you troubleshoot a Kubernetes pod stuck in a CrashLoopBackOff state?

Answer:
A pod in CrashLoopBackOff is repeatedly failing and restarting. Steps to troubleshoot:

1. Check pod events for error messages:

kubectl describe pod my-pod

2. Inspect logs of the failing pod:

kubectl logs my-pod -p

3. Execute into the container to debug runtime issues:

kubectl exec -it my-pod -- /bin/sh

4. Check resource limits: If the pod is being OOMKilled, increase memory requests/limits.

5. Review liveness & readiness probes: A failing probe can cause restarts.

👉 Best Practice: Set an appropriate backoff delay in restartPolicy to prevent excessive restarts.

Repost 🔗 the post if found useful 

Follow Jatin Bansal 


*******************************

25 Blogs to Learn 25 Kubernetes Concepts:

1) Kubernetes Architecture: https://lnkd.in/gmRDrusm
2) POD Lifecycle: https://lnkd.in/g9cbpma4
3) etcd Setup: https://lnkd.in/guD6EeuY
4) etcd Locks: https://lnkd.in/gYbtKsK2
5) crashloopbackoff: https://lnkd.in/gyKyBRt2
6) OOMKilled: https://lnkd.in/gznwimNr
7) ImagePullBackOff: https://lnkd.in/gzCTSWRG
8) CreateContainerConfigError: https://lnkd.in/g6Z5TdBt
9) CreateContainerError: https://lnkd.in/gG_2nHb7
10) RunContainerError: https://lnkd.in/ggQcqi5t
11) Node Disk Pressure: https://lnkd.in/gu9eFiRw
12) Node Not Ready: https://lnkd.in/gksPqZYF
13) Pod Disruption Budget: https://lnkd.in/gNZNxewk
14) RBAC: https://lnkd.in/g2Pr_aA5
15) DNS Optimization: https://lnkd.in/gmNkjZeV
16) Kubernetes Controller: https://lnkd.in/gZ6pkzMt
17) pod.yaml Breakdown: https://lnkd.in/g7yhk_tS
18) Kubernetes Upgrades: https://lnkd.in/g3nwTgwA
19) KEDA vs Karpenter: https://lnkd.in/gED3Vypc
20) Operator vs Helm: https://lnkd.in/gSeg56ME
21) Kubernetes Air Gap: https://lnkd.in/gxxqWdEE
22) QoS Classes: https://lnkd.in/gr_QU8BN 
23) Kubernetes CI/CD: https://lnkd.in/gpk_Et74
24) Deployment Strategies: https://lnkd.in/gdU_8A38
25) Security Contexts: https://lnkd.in/gNQizuFy

42K+ read my free newsletter: https://lnkd.in/gg3RQsRK

What do we cover: 
DevOps, Cloud, Kubernetes, IaC, GitOps, MLOps

🔁 Consider a repost if this is helpful.

![image](https://github.com/user-attachments/assets/774afc08-1852-4e42-a605-0eb298c70a99)



https://www.linkedin.com/posts/govardhana-miriyala-kannaiah_25-blogs-to-learn-25-kubernetes-concepts-activity-7313526946829606913-zZdh?utm_source=share&utm_medium=member_desktop&rcm=ACoAAARSzbgBGEbWHnTkxyPnkFaeZcnK-pW0lqg
