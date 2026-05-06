# Day 20 — CNI — Calico, Flannel, Cilium

> **Phase:** 3 — Networking | **Week:** Week 4 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. CNI Specification
- CNI: Container Network Interface — plugin standard
- kubelet calls CNI plugin on pod create/delete
- Plugin must: assign IP, set up routing, configure iptables
- /etc/cni/net.d/ — CNI config directory

### 2. Flannel
- Simple VXLAN overlay
- No NetworkPolicy support (needs Calico for policies)
- One VXLAN per node, simple routing table
- Use case: simple clusters, dev environments

### 3. Calico
- BGP routing (no overlay by default) — better performance
- Full NetworkPolicy + GlobalNetworkPolicy support
- IPAM with IP pools
- eBPF dataplane option (Calico 3.13+)
- Use case: production, requires NetworkPolicy enforcement

### 4. Cilium
- eBPF-based — no iptables, kernel-level routing
- L7 NetworkPolicy (HTTP, gRPC, Kafka-aware)
- Hubble: built-in network observability
- Use case: modern production, service mesh without sidecar

### 5. How to Choose
- EKS: AWS VPC CNI (default) + Calico for NetworkPolicy
- On-prem: Calico (BGP) or Cilium (eBPF)
- Dev: Flannel or Calico

---

## 🔗 Docs & Resources

- [CNI spec](https://github.com/containernetworking/cni)
- [Calico docs](https://docs.tigera.io/calico/latest/about/)
- [Cilium docs](https://docs.cilium.io/)
- [Flannel](https://github.com/flannel-io/flannel)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install Calico on your kind cluster and inspect its pods and config
- [ ] **Lab 2:** Check Calico routes on a node: `ip route` — see pod CIDR routes
- [ ] **Lab 3:** Install Cilium on a separate cluster and enable Hubble UI
- [ ] **Lab 4:** View live network flows in Hubble
- [ ] **Lab 5:** Debug a CNI issue: delete a CNI pod and observe pod scheduling failure

---

## 🐛 Production Issue to Debug
> After labs

- **PI-19:** All new pods stuck in ContainerCreating — CNI plugin crashlooping

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the CNI specification?
2. What is the main performance difference between Flannel and Calico?
3. What makes Cilium different from Calico?
4. What is eBPF and why does it matter for networking?
5. How would you choose a CNI plugin for a production EKS cluster?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-19
- [ ] Answered interview questions
- [ ] Notes written
