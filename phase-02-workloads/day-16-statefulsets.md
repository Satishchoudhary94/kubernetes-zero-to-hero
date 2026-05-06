# Day 16 — StatefulSets

> **Phase:** 2 — Workloads | **Week:** Week 3 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Why StatefulSets Exist
- Deployments give pods random names and no persistent identity
- Databases need: stable network name, stable storage, ordered startup
- StatefulSet solves all three

### 2. StatefulSet Properties
- Ordered pod names: <name>-0, <name>-1, <name>-2
- Stable network identity: <pod>.<service>.<ns>.svc.cluster.local
- Requires a Headless Service (clusterIP: None)
- volumeClaimTemplates: each pod gets its own PVC
- Ordered startup and shutdown (by default)

### 3. Pod Management Policies
- OrderedReady (default): one at a time, wait for Ready
- Parallel: all pods start/stop simultaneously

### 4. Update Strategies
- RollingUpdate: update from highest ordinal to lowest
- OnDelete: manual update — pod only updated when deleted
- partition: canary update — only update pods >= partition number

### 5. Real-World: StatefulSet for Databases
- MySQL: primary is pod-0, replicas are pod-1, pod-2
- Redis Cluster: 6 pods (3 primary, 3 replica)
- Kafka: broker-0, broker-1, broker-2 with persistent storage

---

## 🔗 Docs & Resources

- [StatefulSets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
- [Running a replicated stateful app](https://kubernetes.io/docs/tasks/run-application/run-replicated-stateful-application/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy a 3-replica StatefulSet with a headless service
- [ ] **Lab 2:** Verify stable DNS: exec into a pod and nslookup other pods by name
- [ ] **Lab 3:** Verify each pod gets its own PVC (volumeClaimTemplates)
- [ ] **Lab 4:** Scale down from 3→1 and observe reverse ordered deletion
- [ ] **Lab 5:** Use partition for a canary update on the StatefulSet
- [ ] **Lab 6:** Deploy MySQL primary + replica using StatefulSet

---

## 🐛 Production Issue to Debug
> After labs

- **PI-15:** StatefulSet pod-1 stuck Pending — PVC failed to provision, diagnose storage issue

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a Deployment and a StatefulSet?
2. Why does a StatefulSet require a Headless Service?
3. What happens to PVCs when you delete a StatefulSet?
4. What is the difference between OrderedReady and Parallel pod management?
5. How would you run a primary-replica MySQL cluster using StatefulSet?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-15
- [ ] Answered interview questions
- [ ] Notes written
