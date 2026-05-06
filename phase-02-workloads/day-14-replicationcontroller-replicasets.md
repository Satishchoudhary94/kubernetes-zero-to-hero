# Day 14 — ReplicationController + ReplicaSets

> **Phase:** 2 — Workloads | **Week:** Week 3 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. ReplicationController (Legacy)
- Ensures N pod replicas are always running
- Only supports equality-based selectors
- Deprecated — replaced by ReplicaSet
- Still appears on CKA exam — know it

### 2. ReplicaSet
- Supports both equality and set-based selectors
- Created and managed by Deployment
- Pod ownership: via labels + ownerReferences
- Selector is immutable after creation

### 3. How ReplicaSet Reconciles
- Counts pods matching selector
- Creates pods if count < desired
- Deletes pods if count > desired
- Orphan adoption: RS adopts pods that match its selector

---

## 🔗 Docs & Resources

- [ReplicationController](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)
- [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a ReplicationController with 3 replicas
- [ ] **Lab 2:** Scale it up/down: `kubectl scale rc <name> --replicas=5`
- [ ] **Lab 3:** Create a ReplicaSet with set-based selector
- [ ] **Lab 4:** Manually delete a pod — watch RS create a replacement
- [ ] **Lab 5:** Create a pod with matching labels BEFORE the RS — observe RS adopts it

---

## 🐛 Production Issue to Debug
> After labs

- **PI-13:** ReplicaSet not creating pods — label selector mismatch with existing pods

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between ReplicationController and ReplicaSet?
2. Why do you almost never create a ReplicaSet directly?
3. What happens if you manually delete a pod managed by a ReplicaSet?
4. What is pod adoption by a ReplicaSet?
5. Why is the ReplicaSet selector immutable?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-13
- [ ] Answered interview questions
- [ ] Notes written
