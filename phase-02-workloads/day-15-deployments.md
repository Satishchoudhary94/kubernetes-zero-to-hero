# Day 15 — Deployments — Complete Guide

> **Phase:** 2 — Workloads | **Week:** Week 3 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Deployment Ownership Chain
- Deployment → creates/manages ReplicaSets → creates/manages Pods
- Old RS kept (with 0 replicas) for rollback history
- revisionHistoryLimit: how many old RS to keep

### 2. Update Strategies
- RollingUpdate (default): maxSurge + maxUnavailable
- Recreate: terminate all, then create all (downtime)
- When to use Recreate: incompatible schema migrations

### 3. Rolling Update Internals
- New RS scaled up, old RS scaled down incrementally
- maxSurge: extra pods above desired (absolute or %)
- maxUnavailable: pods allowed to be unavailable (absolute or %)
- Readiness probe must pass before pod considered available

### 4. Rollbacks
- kubectl rollout undo deployment/<name>
- kubectl rollout undo --to-revision=N
- kubectl rollout history deployment/<name>
- kubectl rollout status: monitor progress

### 5. Pausing and Resuming
- kubectl rollout pause: apply multiple changes as one rollout
- kubectl rollout resume: trigger the combined rollout

---

## 🔗 Docs & Resources

- [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- [Rolling updates](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a Deployment, scale it, update the image
- [ ] **Lab 2:** Observe the rolling update: `kubectl rollout status` + watch RS changes
- [ ] **Lab 3:** Trigger a failed rollout (bad image) and watch it pause
- [ ] **Lab 4:** Rollback to previous version
- [ ] **Lab 5:** Use `kubectl rollout history` to see revision history
- [ ] **Lab 6:** Set maxSurge=0 maxUnavailable=1 and observe strict rolling behavior
- [ ] **Lab 7:** Pause a rollout, make more changes, then resume

---

## 🐛 Production Issue to Debug
> After labs

- **PI-14:** Rolling update stuck — new pods fail readiness probe, old pods never terminate

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. How does a Deployment relate to ReplicaSets?
2. What is the difference between RollingUpdate and Recreate strategies?
3. What is maxSurge and maxUnavailable?
4. How does Kubernetes decide a rolling update has succeeded?
5. How do you roll back a Deployment to a specific revision?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-14
- [ ] Answered interview questions
- [ ] Notes written
