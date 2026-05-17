# Day 57 — Systematic Debugging Methodology

> **Phase:** 9 — Troubleshooting | **Week:** Week 11 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. The 5-Layer Debugging Model
- Layer 1 — Pod: is the container running? logs? events?
- Layer 2 — Node: is the node healthy? resources? kubelet?
- Layer 3 — Network: can pods communicate? DNS working? Services?
- Layer 4 — Storage: is the PVC bound? volume mounted?
- Layer 5 — Control Plane: API server, etcd, scheduler healthy?

### 2. First Steps for Any Issue
- kubectl get <resource> — what's the current state?
- kubectl describe <resource> — Events section is the key
- kubectl logs <pod> — app-level errors
- kubectl logs <pod> --previous — logs from crashed container
- kubectl get events --sort-by=.lastTimestamp -n <namespace>

### 3. Decision Tree by Symptom
- Pod not running → check phase, conditions, events
- Service not reachable → check endpoints, DNS, kube-proxy
- Storage issue → check PVC status, PV binding, StorageClass
- Scaling not working → check HPA, metrics-server, resource requests
- Auth failing → check RBAC, ServiceAccount, token

### 4. Speed for CKA Exam
- Practice: 10-minute timed debugging challenges
- Muscle memory: go to Events first, always
- kubectl explain: look up field names without docs
- Aliases: k=kubectl, kgp=kubectl get pods

---

## 🔗 Docs & Resources

- [Troubleshooting applications](https://kubernetes.io/docs/tasks/debug/debug-application/)
- [Troubleshooting clusters](https://kubernetes.io/docs/tasks/debug/debug-cluster/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Set up kubectl aliases: k, kgp, kgn, kd, kl
- [ ] **Lab 2:** Practice the decision tree: given a symptom, write the first 3 commands
- [ ] **Lab 3:** Timed drill: given a broken pod, find the issue in under 5 minutes
- [ ] **Lab 4:** Timed drill: given a broken Service, find the issue in under 5 minutes
- [ ] **Lab 5:** Document your personal debugging runbook

---

## 🐛 Production Issue to Debug
> After labs

- **PI-general:** Mystery broken environment: 5 unknown issues, find and fix all in 30 minutes

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the first 3 commands you run when a pod is not starting?
2. Where do you look first for clues about a broken resource?
3. What does `kubectl get events --sort-by=.lastTimestamp` show you?
4. How do you see logs from a container that has already crashed?
5. Walk me through debugging a Service that returns connection refused.

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-general
- [ ] Answered interview questions
- [ ] Notes written
