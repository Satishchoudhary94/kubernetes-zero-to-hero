# Day 03 — Kubernetes Architecture — Complete Mental Model

> **Phase:** 1 — Foundation | **Week:** Week 1 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. High-Level Cluster Overview
- Control plane nodes vs worker nodes
- The declarative model: desired state vs actual state
- The reconciliation loop — the heart of Kubernetes
- Why Kubernetes is self-healing

### 2. Control Plane Components
- kube-apiserver — the only entry point
- etcd — the cluster brain/memory
- kube-scheduler — pod placement
- kube-controller-manager — reconciliation loops
- cloud-controller-manager — cloud provider bridge

### 3. Worker Node Components
- kubelet — node agent, manages pod lifecycle
- kube-proxy — network rules (iptables/IPVS)
- Container runtime (containerd/CRI-O)

### 4. Full Request Flow
- kubectl apply → API server → etcd → controllers → scheduler → kubelet
- Each step's responsibility
- What happens when each component is down

### 5. cloud-controller-manager
- Bridges Kubernetes and cloud provider APIs
- On EKS: creates ALB/NLB, EBS volumes, manages node lifecycle
- Node controller, route controller, service controller

---

## 🔗 Docs & Resources

- [Kubernetes Architecture docs](https://kubernetes.io/docs/concepts/architecture/)
- [cloud-controller-manager](https://kubernetes.io/docs/concepts/architecture/cloud-controller/)
- [Kubernetes components overview](https://kubernetes.io/docs/concepts/overview/components/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Set up kind multi-node cluster (1 control-plane + 2 workers)
- [ ] **Lab 2:** Inspect all control plane pods: `kubectl get pods -n kube-system`
- [ ] **Lab 3:** Trace the request flow: `kubectl run nginx --image=nginx` and watch events
- [ ] **Lab 4:** Watch the reconciliation loop: delete a pod from a deployment, observe auto-replace
- [ ] **Lab 5:** Explore etcd keys: exec into etcd pod and use etcdctl get /registry --prefix --keys-only
- [ ] **Lab 6:** Examine kubeconfig: understand clusters, users, contexts

---

## 🐛 Production Issue to Debug
> After labs

- **PI-01:** Scheduler down — pods stuck in Pending forever, how to diagnose and recover

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the role of the API server in Kubernetes?
2. What happens if etcd goes down?
3. What is the reconciliation loop and why is it important?
4. What is the difference between kube-proxy and a CNI plugin?
5. What does cloud-controller-manager do on EKS?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-01
- [ ] Answered interview questions
- [ ] Notes written
