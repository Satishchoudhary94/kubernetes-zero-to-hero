# Day 10 — Labels, Selectors, Annotations

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. Labels
- Key-value pairs for identifying and organizing resources
- Key format: optional prefix/name (e.g., app.kubernetes.io/name)
- Recommended labels: app, version, component, managed-by, part-of
- Labels are queryable — the basis for all selectors

### 2. Selectors
- Equality-based: app=nginx, tier!=frontend
- Set-based: app in (nginx,apache), env notin (prod)
- Used by: Services, ReplicaSets, Deployments, NetworkPolicies
- Label selectors are immutable on ReplicaSets

### 3. Annotations
- Non-identifying metadata — not used for selection
- Used by: Ingress controllers (routing rules), Prometheus (scrape config)
- ALB Ingress annotations: alb.ingress.kubernetes.io/*
- Can hold larger/more complex values than labels

### 4. Real-World Usage Patterns
- Canary deployments via label-based traffic splitting
- Blue-green via Service selector swap
- Cost allocation tags mirrored as labels
- Environment segregation: env=prod vs env=staging

---

## 🔗 Docs & Resources

- [Labels and selectors](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
- [Recommended labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/common-labels/)
- [Annotations](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Label 10 pods across 3 namespaces, then filter using equality and set-based selectors
- [ ] **Lab 2:** Create a Service and intentionally mismatch the selector — observe traffic failure
- [ ] **Lab 3:** Add Prometheus scrape annotations to a pod and verify with `kubectl get pod -o yaml`
- [ ] **Lab 4:** Use `kubectl get pods -l 'app in (frontend,backend)' -A` to filter across namespaces
- [ ] **Lab 5:** Simulate a blue-green switch by updating a Service selector

---

## 🐛 Production Issue to Debug
> After labs

- **PI-08:** Service not routing to pods — selector mismatch, systematic debugging

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between labels and annotations?
2. What are equality-based vs set-based selectors?
3. Why are label selectors on a ReplicaSet immutable?
4. How does Prometheus use annotations?
5. How would you implement a blue-green deployment using only label selectors?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-08
- [ ] Answered interview questions
- [ ] Notes written
