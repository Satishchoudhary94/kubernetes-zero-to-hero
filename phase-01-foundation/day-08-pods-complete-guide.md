# Day 08 — Pods — Complete Guide

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Pod Fundamentals
- Pod: smallest deployable unit in Kubernetes
- One or more containers sharing network + storage
- Pod IP: unique, flat, no NAT
- Pause container (sandbox): holds the network namespace

### 2. Pod Spec Anatomy
- containers[]: name, image, ports, resources, env, volumeMounts
- volumes[]: types — emptyDir, configMap, secret, hostPath, PVC
- restartPolicy: Always, OnFailure, Never
- terminationGracePeriodSeconds
- imagePullPolicy: Always, IfNotPresent, Never

### 3. Multi-Container Pod Patterns
- Sidecar: enhance or extend main container
- Ambassador: proxy outbound traffic
- Adapter: transform output for monitoring
- Containers communicate via localhost + shared volumes

### 4. Resource Requests and Limits
- requests: what the scheduler uses for placement
- limits: hard cap enforced by cgroups
- CPU: throttled when over limit (not killed)
- Memory: OOMKilled when over limit
- QoS classes: Guaranteed, Burstable, BestEffort

---

## 🔗 Docs & Resources

- [Pod docs](https://kubernetes.io/docs/concepts/workloads/pods/)
- [Resource management](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)
- [Multi-container pods](https://kubernetes.io/docs/concepts/workloads/pods/#how-pods-manage-multiple-containers)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a pod YAML from scratch (no generators) with all key fields
- [ ] **Lab 2:** Build a multi-container pod: nginx + a log-tail sidecar
- [ ] **Lab 3:** Set resource requests and limits, then trigger OOMKill intentionally
- [ ] **Lab 4:** Share data between containers using an emptyDir volume
- [ ] **Lab 5:** Use `kubectl exec` to connect to specific container in multi-container pod
- [ ] **Lab 6:** Inspect pod sandbox (pause container) using crictl

---

## 🐛 Production Issue to Debug
> After labs

- **PI-06:** OOMKilled — container killed by kernel, diagnose memory limit and fix

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the pause container and why does every pod have one?
2. What is the difference between resource requests and limits?
3. How do containers in the same pod communicate?
4. What is the difference between QoS class Guaranteed vs Burstable?
5. What happens when a container exceeds its memory limit?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-06
- [ ] Answered interview questions
- [ ] Notes written
