# Day 17 — DaemonSets

> **Phase:** 2 — Workloads | **Week:** Week 3 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. DaemonSet Purpose
- Runs one pod per node (or per selected subset of nodes)
- As nodes are added, pods are automatically scheduled
- As nodes are removed, pods are garbage collected

### 2. Real-World Use Cases
- Log collection: Fluent Bit, Fluentd
- Node monitoring: node-exporter, Datadog agent
- CNI plugin pods (Calico, Cilium)
- Storage: Ceph OSD, Longhorn
- Security: Falco, Wazuh agent

### 3. Node Targeting
- nodeSelector: only run on matching nodes
- Affinity/Anti-affinity: more expressive targeting
- Tolerations: run on tainted nodes (e.g., GPU nodes)

### 4. Update Strategies
- RollingUpdate (default): maxUnavailable
- OnDelete: manually delete pods to trigger update

---

## 🔗 Docs & Resources

- [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)
- [Running a DaemonSet](https://kubernetes.io/docs/tasks/manage-daemon/update-daemon-set/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy a Fluent Bit DaemonSet that collects logs from all nodes
- [ ] **Lab 2:** Verify one pod per node: `kubectl get pods -o wide`
- [ ] **Lab 3:** Add a new node to the cluster — verify DaemonSet pod auto-created
- [ ] **Lab 4:** Taint a node and verify DaemonSet pod is NOT created (no toleration)
- [ ] **Lab 5:** Add toleration to DaemonSet spec — verify pod now runs on tainted node

---

## 🐛 Production Issue to Debug
> After labs

- **PI-16:** DaemonSet pod missing on one node — node has taint without matching toleration

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is a DaemonSet and when would you use it?
2. How is a DaemonSet different from a Deployment?
3. How do you run a DaemonSet only on a subset of nodes?
4. What happens to DaemonSet pods when a node is drained?
5. Name 3 real-world uses for DaemonSets.

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-16
- [ ] Answered interview questions
- [ ] Notes written
