# Day 41 — HPA — Horizontal Pod Autoscaler

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. HPA Fundamentals
- Automatically scales pod replicas based on metrics
- Metrics sources: CPU, memory, custom metrics, external metrics
- HPA controller runs in kube-controller-manager
- Scale-up: aggressive (fast). Scale-down: conservative (slow, stabilization)

### 2. CPU-Based Scaling
- targetAverageUtilization: % of requested CPU
- Metrics source: metrics-server (must be installed)
- Algorithm: desiredReplicas = ceil(current * (currentMetric / desiredMetric))

### 3. Custom + External Metrics
- Custom: prometheus-adapter exposes Prometheus metrics to HPA
- External: metrics outside cluster (SQS depth, Pub/Sub lag)
- HPA v2 API: supports multiple metrics simultaneously

### 4. Scaling Behavior Tuning
- scaleDown.stabilizationWindowSeconds: prevent flapping (default 300s)
- scaleUp.policies: control how fast to add pods
- minReplicas / maxReplicas bounds

---

## 🔗 Docs & Resources

- [HPA](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
- [HPA walkthrough](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install metrics-server
- [ ] **Lab 2:** Create HPA on a Deployment with CPU target 50%
- [ ] **Lab 3:** Load test with `kubectl run load --image=busybox -- /bin/sh -c 'while true; do wget -q -O- http://svc; done'`
- [ ] **Lab 4:** Watch HPA scale up: `kubectl get hpa -w`
- [ ] **Lab 5:** Stop the load and watch scale-down (observe stabilization window)
- [ ] **Lab 6:** Create HPA with custom metric (Prometheus query via prometheus-adapter)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-41:** HPA stuck at minReplicas — metrics-server not installed, debug missing metrics

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. How does HPA decide how many replicas to create?
2. What is the stabilization window and why does it exist?
3. What is the difference between CPU-based and custom metrics HPA?
4. What must be installed for basic CPU-based HPA to work?
5. How do you prevent HPA from scaling down too aggressively?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-41
- [ ] Answered interview questions
- [ ] Notes written
