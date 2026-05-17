# Day 45 — ResourceQuota + LimitRange + PriorityClass

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. ResourceQuota — Namespace Limits
- Covered in Day 11 — deep extension here
- Scopes: BestEffort, NotBestEffort, Terminating, NotTerminating
- Resource quota for extended resources (GPU, custom)
- Object count quotas: max pods, services, PVCs per namespace

### 2. LimitRange — Container Defaults
- Default requests/limits for containers that don't specify
- Max/min constraints: reject pods outside the range
- LimitRange for PVC: restrict storage request size

### 3. PriorityClass
- Assign numerical priority to pods
- Higher priority pods preempt lower priority pods
- system-cluster-critical: 2000000000 (control plane pods)
- system-node-critical: 2000001000
- Create custom: low-priority for batch, high-priority for user-facing
- preemptionPolicy: PreemptLowerPriority vs Never

### 4. QoS Classes and Eviction
- Guaranteed: requests == limits → last to be evicted
- Burstable: requests < limits → evicted second
- BestEffort: no requests/limits → evicted first
- Pod eviction order under node memory pressure

---

## 🔗 Docs & Resources

- [Resource Quotas](https://kubernetes.io/docs/concepts/policy/resource-quotas/)
- [PriorityClass](https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/)
- [Node pressure eviction](https://kubernetes.io/docs/concepts/scheduling-eviction/node-pressure-eviction/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create high-priority and low-priority PriorityClasses
- [ ] **Lab 2:** Exhaust node resources with low-priority pods
- [ ] **Lab 3:** Create a high-priority pod — watch it preempt low-priority pods
- [ ] **Lab 4:** Simulate memory pressure: see BestEffort pods evicted first
- [ ] **Lab 5:** Set ResourceQuota with scopes: BestEffort gets 0 CPU allowed

---

## 🐛 Production Issue to Debug
> After labs

- **PI-45:** Critical pod not starting — node at capacity, set PriorityClass to preempt batch pods

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the eviction order for pods under memory pressure?
2. What is a PriorityClass and how does preemption work?
3. What is the difference between ResourceQuota scopes?
4. How do QoS classes relate to eviction?
5. What PriorityClass do system-critical pods use?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-45
- [ ] Answered interview questions
- [ ] Notes written
