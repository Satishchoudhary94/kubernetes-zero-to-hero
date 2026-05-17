# Day 59 — Node-Level Debugging

> **Phase:** 9 — Troubleshooting | **Week:** Week 11 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Node Not Ready
- kubectl describe node: check Conditions section
- MemoryPressure, DiskPressure, PIDPressure, NetworkUnavailable
- kubelet not running: journalctl -u kubelet on node
- Node unreachable: check EC2 instance status in AWS console

### 2. Node Pressure Conditions
- DiskPressure: disk full — evicts BestEffort pods
- MemoryPressure: memory full — evicts pods in QoS order
- PIDPressure: too many processes — rare but critical
- Check: df -h, free -m, cat /proc/sys/kernel/pid_max

### 3. Node-Level Tools (crictl)
- crictl ps — list containers on node
- crictl logs <id> — container logs
- crictl inspect <id> — container config
- crictl stopp / rmp — stop pod sandbox

### 4. Draining and Cordoning
- kubectl cordon: mark unschedulable (don't schedule new pods)
- kubectl drain: cordon + evict all pods (for maintenance)
- --ignore-daemonsets, --delete-emptydir-data flags
- kubectl uncordon: re-enable scheduling

---

## 🔗 Docs & Resources

- [Node debugging](https://kubernetes.io/docs/tasks/debug/debug-cluster/)
- [kubectl debug node](https://kubernetes.io/docs/tasks/debug/debug-cluster/kubectl-node-debug/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Simulate DiskPressure: fill disk on a node, observe pod eviction
- [ ] **Lab 2:** Use `kubectl debug node/<name>` to get a privileged pod on the node
- [ ] **Lab 3:** Inspect kubelet logs: `journalctl -u kubelet -n 50`
- [ ] **Lab 4:** Drain a node, verify pods rescheduled, then uncordon
- [ ] **Lab 5:** Use crictl to list containers and inspect a specific container

---

## 🐛 Production Issue to Debug
> After labs

- **PI-58:** Node DiskPressure causing cascade evictions — find large files, clean up, restore

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What does kubectl cordon do and when would you use it?
2. What is the difference between cordon and drain?
3. How do you get a root shell on a Kubernetes node without SSH?
4. What causes DiskPressure on a node?
5. How do you check kubelet logs on a node?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-58
- [ ] Answered interview questions
- [ ] Notes written
