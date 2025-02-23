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
