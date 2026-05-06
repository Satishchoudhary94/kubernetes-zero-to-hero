# Day 23 — CoreDNS Deep Dive

> **Phase:** 3 — Networking | **Week:** Week 4 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. DNS in Kubernetes
- Every pod gets /etc/resolv.conf injected by kubelet
- nameserver points to CoreDNS ClusterIP
- search domains: default.svc.cluster.local svc.cluster.local cluster.local
- FQDN format: <svc>.<ns>.svc.<cluster-domain>

### 2. CoreDNS Architecture
- Runs as Deployment (2 replicas for HA)
- Corefile: plugin-based configuration
- Key plugins: errors, health, ready, kubernetes, forward, cache
- kubernetes plugin: serves in-cluster DNS from API server watch
- forward plugin: upstream DNS for external queries

### 3. ndots Problem (Performance)
- ndots:5 default: 5 search domain attempts before absolute lookup
- External DNS lookup does 5 failed queries before succeeding
- Fix: use FQDN with trailing dot OR reduce ndots to 2
- dnsConfig in pod spec to override

### 4. NodeLocal DNSCache
- Runs a DNS cache on each node (DaemonSet)
- Avoids conntrack table exhaustion at scale
- Reduces CoreDNS load significantly
- Uses link-local IP: 169.254.20.10

---

## 🔗 Docs & Resources

- [CoreDNS](https://coredns.io/manual/toc/)
- [DNS in Kubernetes](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)
- [NodeLocal DNSCache](https://kubernetes.io/docs/tasks/administer-cluster/nodelocaldns/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Exec into a pod and run `cat /etc/resolv.conf`
- [ ] **Lab 2:** Resolve a service: `nslookup <svc>.<ns>.svc.cluster.local`
- [ ] **Lab 3:** Trace an external DNS query: watch CoreDNS logs during a curl to google.com
- [ ] **Lab 4:** Observe ndots in action: use `dig +search google.com` to see all attempts
- [ ] **Lab 5:** Configure a pod with custom dnsConfig (ndots: 2)
- [ ] **Lab 6:** Deploy NodeLocal DNSCache and verify pod resolv.conf changes

---

## 🐛 Production Issue to Debug
> After labs

- **PI-22:** DNS resolution failing for all pods — CoreDNS pod crashlooping, diagnose and restore

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the FQDN format for a Kubernetes service?
2. What is the ndots problem and how do you fix it?
3. What is NodeLocal DNSCache and why is it used?
4. How do you debug DNS issues inside a pod?
5. What plugins does CoreDNS use for cluster DNS?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-22
- [ ] Answered interview questions
- [ ] Notes written
