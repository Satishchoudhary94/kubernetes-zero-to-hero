# Day 46 — Topology Spread Constraints

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. Problem: Uneven Pod Distribution
- Without constraints: scheduler may pile pods on one zone/node
- One zone failure = majority of pods gone
- Topology spread: explicitly control distribution

### 2. Topology Spread Constraints
- maxSkew: max allowed difference between most/least loaded topology
- topologyKey: what to spread across (zone, node, rack)
- whenUnsatisfiable: DoNotSchedule (hard) or ScheduleAnyway (soft)
- labelSelector: which pods to consider for balance
- matchLabelKeys (K8s 1.27+): spread per rolling update

### 3. Multi-AZ Production Pattern
- Spread 6 replicas across 3 AZs: max 2 per zone
- topologyKey: topology.kubernetes.io/zone
- maxSkew: 1 — zones differ by at most 1 pod

### 4. Combining with Pod Anti-Affinity
- Topology spread: ensures even distribution
- Anti-affinity: ensures no two replicas on same node
- Use both together for maximum resilience

---

## 🔗 Docs & Resources

- [Topology Spread Constraints](https://kubernetes.io/docs/concepts/scheduling-eviction/topology-spread-constraints/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create 3-node kind cluster with zone labels
- [ ] **Lab 2:** Deploy 6 replicas with topology spread across zones (maxSkew: 1)
- [ ] **Lab 3:** Verify distribution: `kubectl get pods -o wide`
- [ ] **Lab 4:** Kill one zone's node — observe rebalancing
- [ ] **Lab 5:** Combine topology spread + pod anti-affinity
- [ ] **Lab 6:** Use DoNotSchedule vs ScheduleAnyway — observe difference

---

## 🐛 Production Issue to Debug
> After labs

- **PI-46:** Pods all in one zone after scale-up — topology spread not applied to existing pods

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is maxSkew in topology spread constraints?
2. What is the difference between DoNotSchedule and ScheduleAnyway?
3. How do you spread pods across availability zones?
4. What is topologyKey and what labels does it use?
5. Should you use topology spread OR pod anti-affinity — or both?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-46
- [ ] Answered interview questions
- [ ] Notes written
