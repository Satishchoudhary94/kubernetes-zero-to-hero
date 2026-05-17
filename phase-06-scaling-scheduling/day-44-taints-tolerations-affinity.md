# Day 44 — Taints, Tolerations, Node Affinity

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Taints and Tolerations
- Taint: marks a node to repel pods
- Toleration: allows a pod to be scheduled on a tainted node
- Effects: NoSchedule, PreferNoSchedule, NoExecute
- NoExecute: evicts existing pods that don't tolerate
- Use cases: GPU nodes, Spot instances, dedicated nodes

### 2. Node Affinity
- requiredDuringSchedulingIgnoredDuringExecution: hard requirement
- preferredDuringSchedulingIgnoredDuringExecution: soft preference
- matchExpressions: label-based node selection
- Replaces nodeSelector (more expressive)

### 3. Pod Affinity + Anti-Affinity
- podAffinity: schedule near specific pods (same node/zone)
- podAntiAffinity: schedule away from specific pods
- topologyKey: what 'near' means (kubernetes.io/hostname, topology.kubernetes.io/zone)
- Use case: anti-affinity to spread replicas across AZs

### 4. Real-World Patterns
- GPU nodes: taint + toleration for ML workloads
- Spot nodes: taint + toleration for fault-tolerant batch
- Dedicated nodes: taint + toleration + nodeAffinity combined
- Multi-AZ spread: podAntiAffinity with zone topologyKey

---

## 🔗 Docs & Resources

- [Taints and Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/)
- [Node Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Taint a node with NoSchedule — verify new pods not scheduled there
- [ ] **Lab 2:** Add toleration to a pod — verify it schedules on tainted node
- [ ] **Lab 3:** Use NoExecute taint and watch existing pods get evicted
- [ ] **Lab 4:** Create nodeAffinity: require pods on nodes labeled zone=us-east-1a
- [ ] **Lab 5:** Create podAntiAffinity: spread 5 replicas across 3 nodes
- [ ] **Lab 6:** Simulate: GPU node pool with taint, ML pod with toleration

---

## 🐛 Production Issue to Debug
> After labs

- **PI-44:** All deployment pods land on one node — podAntiAffinity misconfigured, debug and fix

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between NoSchedule and NoExecute?
2. How does toleration differ from node affinity?
3. When would you use pod anti-affinity?
4. What is topologyKey and what values does it commonly take?
5. How do you dedicate a node to a specific workload type?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-44
- [ ] Answered interview questions
- [ ] Notes written
