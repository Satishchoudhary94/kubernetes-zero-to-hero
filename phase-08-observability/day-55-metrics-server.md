# Day 55 — Metrics Server + Custom Metrics API

> **Phase:** 8 — Observability | **Week:** Week 10 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. Metrics Server
- Lightweight resource metrics (CPU/memory) for kubectl top and HPA
- NOT for long-term storage — use Prometheus for that
- Deployed as Deployment, scrapes kubelet /stats/summary
- Required for: kubectl top pods/nodes, HPA CPU scaling

### 2. Metrics API Architecture
- Core metrics API: metrics.k8s.io/v1beta1 (CPU/memory — metrics-server)
- Custom metrics API: custom.metrics.k8s.io (app metrics — prometheus-adapter)
- External metrics API: external.metrics.k8s.io (cloud metrics — KEDA)
- HPA reads from all three

### 3. Prometheus Adapter
- Bridges Prometheus metrics → Custom Metrics API
- Rules: map PromQL queries to metric names
- HPA can then scale on custom.metrics.k8s.io/<metric>

---

## 🔗 Docs & Resources

- [Metrics Server](https://github.com/kubernetes-sigs/metrics-server)
- [Custom metrics API](https://github.com/kubernetes/metrics/blob/master/IMPLEMENTATIONS.md)
- [Prometheus Adapter](https://github.com/kubernetes-sigs/prometheus-adapter)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install metrics-server, run `kubectl top pods` and `kubectl top nodes`
- [ ] **Lab 2:** Install prometheus-adapter with a custom metric rule
- [ ] **Lab 3:** Verify custom metric appears: `kubectl get --raw /apis/custom.metrics.k8s.io/v1beta1`
- [ ] **Lab 4:** Create HPA that scales on custom metric (requests per second)
- [ ] **Lab 5:** Load test and observe HPA scaling on custom metric

---

## 🐛 Production Issue to Debug
> After labs

- **PI-56:** kubectl top returns no metrics — metrics-server pod has wrong kubelet TLS config

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between metrics-server and Prometheus?
2. What are the 3 metrics APIs in Kubernetes?
3. What is prometheus-adapter?
4. How does HPA use the custom metrics API?
5. How do you verify a custom metric is available?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-56
- [ ] Answered interview questions
- [ ] Notes written
