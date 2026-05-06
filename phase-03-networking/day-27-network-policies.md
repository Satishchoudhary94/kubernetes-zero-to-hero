# Day 27 — Network Policies — Zero-Trust Networking

> **Phase:** 3 — Networking | **Week:** Week 5 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Default Behavior (No NetworkPolicy)
- All pods can communicate with all pods by default
- No isolation between namespaces by default
- Any pod can reach any service

### 2. NetworkPolicy Model
- Whitelist model: once a NetworkPolicy selects a pod, only allowed traffic passes
- podSelector: which pods this policy applies to
- policyTypes: Ingress, Egress, or both
- Rules: namespaceSelector, podSelector, ipBlock, ports

### 3. Default-Deny Patterns
- Default-deny all ingress: empty podSelector + policyTypes: [Ingress]
- Default-deny all egress: empty podSelector + policyTypes: [Egress]
- Apply to every namespace in production

### 4. Real-World Patterns
- Only backend can reach database (not frontend)
- Monitoring namespace can scrape all namespaces
- Allow egress to DNS only (CoreDNS)
- Allow egress to specific external IPs (ipBlock)

### 5. Limitations
- NetworkPolicy only works if CNI supports it (Calico, Cilium, not Flannel alone)
- No L7 policy (use Cilium or Istio for HTTP-level)

---

## 🔗 Docs & Resources

- [NetworkPolicy](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
- [NetworkPolicy recipes](https://github.com/ahmetb/kubernetes-network-policy-recipes)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy frontend + backend + database pods
- [ ] **Lab 2:** Apply default-deny-all to the namespace
- [ ] **Lab 3:** Add policy: only backend can reach database on port 5432
- [ ] **Lab 4:** Add policy: frontend can reach backend on port 3000
- [ ] **Lab 5:** Verify: frontend cannot reach database directly
- [ ] **Lab 6:** Use netshoot image to test connectivity: `kubectl run test --image=nicolaka/netshoot`
- [ ] **Lab 7:** Allow monitoring namespace to scrape all pods on port 9090

---

## 🐛 Production Issue to Debug
> After labs

- **PI-26:** Microservice can't reach database after NetworkPolicy applied — debug policy rules

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the default network behavior in Kubernetes without any NetworkPolicy?
2. How does the whitelist model work in NetworkPolicy?
3. What is a default-deny policy and how do you implement it?
4. Which CNI plugins support NetworkPolicy?
5. How do you debug a NetworkPolicy blocking traffic?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-26
- [ ] Answered interview questions
- [ ] Notes written
