# Day 11 — Namespaces + Resource Isolation

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Namespaces Fundamentals
- Logical partitions within a cluster
- Namespace-scoped vs cluster-scoped resources
- Default namespaces: default, kube-system, kube-public, kube-node-lease
- DNS scoping: service.namespace.svc.cluster.local

### 2. ResourceQuota
- Limit total resources per namespace
- CPU, memory, storage, object count (pods, services, PVCs)
- Hard limits: request exceeding quota = rejected
- Check usage: kubectl describe resourcequota -n <ns>

### 3. LimitRange
- Set defaults and limits per container/pod
- default: applied when container has no requests/limits
- max/min: enforce boundaries
- Container type vs Pod type vs PVC type

### 4. Multi-Tenancy Patterns
- Namespace-per-team or namespace-per-environment
- Combining ResourceQuota + LimitRange + RBAC + NetworkPolicy
- Soft multi-tenancy vs hard multi-tenancy
- Virtual clusters (vcluster) for hard isolation

---

## 🔗 Docs & Resources

- [Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
- [ResourceQuota](https://kubernetes.io/docs/concepts/policy/resource-quotas/)
- [LimitRange](https://kubernetes.io/docs/concepts/policy/limit-range/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create 3 namespaces: dev, staging, prod
- [ ] **Lab 2:** Apply ResourceQuota to each (different limits per env)
- [ ] **Lab 3:** Apply LimitRange with container defaults to staging
- [ ] **Lab 4:** Try to exceed the quota — observe the rejection error
- [ ] **Lab 5:** Create a pod with no requests/limits in staging — observe LimitRange defaults applied
- [ ] **Lab 6:** List all resources across all namespaces: `kubectl get all -A`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-09:** Deployment failing — ResourceQuota exceeded, how to identify and resolve

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between namespace-scoped and cluster-scoped resources?
2. What happens if you try to create a pod that exceeds the namespace ResourceQuota?
3. What is a LimitRange and how does it differ from ResourceQuota?
4. How does DNS resolution differ for a service in the same vs different namespace?
5. What are the trade-offs of namespace-per-team vs namespace-per-environment?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-09
- [ ] Answered interview questions
- [ ] Notes written
