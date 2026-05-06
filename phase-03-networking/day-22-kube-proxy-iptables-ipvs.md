# Day 22 — kube-proxy — iptables vs IPVS

> **Phase:** 3 — Networking | **Week:** Week 4 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. kube-proxy Role
- Runs on every node as DaemonSet
- Watches Services and EndpointSlices
- Programs network rules to implement Service VIP

### 2. iptables Mode
- Uses DNAT rules in iptables nat table
- Random load balancing via probability rules
- KUBE-SERVICES chain → KUBE-SVC-* chain → KUBE-SEP-* chain
- Problem: O(n) rule scanning, slow at >1000 services

### 3. IPVS Mode
- Uses Linux kernel IPVS (IP Virtual Server)
- Hash table lookup — O(1) regardless of rule count
- Supports multiple LB algorithms: rr, lc, dh, sh, sed, nq
- Requires kernel modules: ip_vs, ip_vs_rr, nf_conntrack
- Recommended for clusters with >1000 services

### 4. Switching Modes
- Edit kube-proxy ConfigMap: mode: ipvs
- Verify: `ipvsadm -Ln` on a node

---

## 🔗 Docs & Resources

- [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/)
- [Virtual IPs and service proxies](https://kubernetes.io/docs/reference/networking/virtual-ips/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Inspect iptables KUBE-SERVICES chain on a node
- [ ] **Lab 2:** Trace a ClusterIP request through iptables rules
- [ ] **Lab 3:** Switch kube-proxy to IPVS mode
- [ ] **Lab 4:** Verify IPVS rules with `ipvsadm -Ln`
- [ ] **Lab 5:** Benchmark: measure DNS/service lookup time in both modes (optional)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-21:** Service routing intermittently fails — kube-proxy rules not updated after pod restart

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What does kube-proxy do?
2. How does ClusterIP service routing work in iptables mode?
3. Why is IPVS better than iptables at scale?
4. At what scale should you switch to IPVS mode?
5. How do you verify kube-proxy is in IPVS mode?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-21
- [ ] Answered interview questions
- [ ] Notes written
