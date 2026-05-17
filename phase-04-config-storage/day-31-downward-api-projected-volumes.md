# Day 31 — Downward API + Projected Volumes

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. Downward API
- Exposes pod/container metadata to the running container
- Available as: environment variables or volume files
- Pod info: name, namespace, IP, node name, labels, annotations
- Container info: CPU/memory requests and limits

### 2. Use Cases
- App logs its own pod name for tracing
- App reports its node for topology awareness
- App knows its own resource limits for tuning

### 3. Projected Volumes
- Combine multiple volume sources into one mount point
- Sources: secret, configMap, downwardAPI, serviceAccountToken
- Cleaner than mounting each separately

### 4. Service Account Token Projection
- Short-lived, auto-rotated tokens (vs legacy long-lived tokens)
- audience: specify token audience for security
- expirationSeconds: token lifetime
- Required for IRSA on EKS

---

## 🔗 Docs & Resources

- [Downward API](https://kubernetes.io/docs/concepts/workloads/pods/downward-api/)
- [Projected volumes](https://kubernetes.io/docs/concepts/storage/projected-volumes/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a pod that logs its own name, namespace, and node IP via Downward API env vars
- [ ] **Lab 2:** Mount pod labels and annotations as files using Downward API volume
- [ ] **Lab 3:** Create a projected volume combining configMap + secret + downwardAPI
- [ ] **Lab 4:** Use projected service account token (audience + expirationSeconds)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-30:** App cannot determine its own pod name — Downward API env var missing from spec

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the Downward API used for?
2. What is the difference between Downward API as env var vs volume file?
3. What is a projected volume?
4. What are projected service account tokens and why are they better than legacy tokens?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 4 labs
- [ ] Debugged PI-30
- [ ] Answered interview questions
- [ ] Notes written
