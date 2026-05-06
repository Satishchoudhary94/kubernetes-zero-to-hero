# Day 13 — Static Pods

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. What are Static Pods
- Managed directly by kubelet, not the API server
- Defined in /etc/kubernetes/manifests/ on the node
- kubelet watches this directory — add/edit/delete = immediate effect
- Mirror pod: read-only copy visible in API server (cannot be deleted via API)

### 2. How Control Plane Uses Static Pods
- kube-apiserver, etcd, kube-scheduler, kube-controller-manager are ALL static pods
- This means they can start even before the cluster is fully running
- How to modify control plane config: edit the static pod manifest

### 3. Static Pods in CKA
- Common exam task: create a static pod on a specific node
- Recover a broken control plane by fixing the static pod manifest
- Know the default manifests directory path

---

## 🔗 Docs & Resources

- [Static pods](https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/)
- [kubeadm control plane](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a static pod by placing a YAML in /etc/kubernetes/manifests/
- [ ] **Lab 2:** Try to delete the mirror pod via kubectl — observe it respawns
- [ ] **Lab 3:** Edit the static pod manifest and watch kubelet apply the change
- [ ] **Lab 4:** Break the kube-apiserver static pod manifest and then fix it
- [ ] **Lab 5:** Identify all static pods in your cluster

---

## 🐛 Production Issue to Debug
> After labs

- **PI-12:** kube-apiserver not starting after upgrade — static pod manifest has wrong image tag

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is a static pod and how is it different from a regular pod?
2. Why are control plane components run as static pods?
3. What is a mirror pod?
4. How would you modify the kube-apiserver configuration in a kubeadm cluster?
5. What happens if you delete a static pod manifest from the node?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-12
- [ ] Answered interview questions
- [ ] Notes written
