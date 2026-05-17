# Day 43 — KEDA — Event-Driven Autoscaling

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Why KEDA Exists
- HPA only scales on CPU/memory (or custom metrics API)
- KEDA: scale on any event source — SQS, Kafka, Prometheus, cron
- Scale to zero: no messages = 0 pods (serverless-like)

### 2. KEDA Architecture
- KEDA operator + metrics adapter
- ScaledObject: for Deployments/StatefulSets
- ScaledJob: for Job-based workloads (one job per event)
- Scalers: 50+ built-in scalers

### 3. Key Scalers
- AWS SQS: scale on queue depth
- Kafka: scale on consumer group lag
- Prometheus: scale on any PromQL query
- Cron: scale on time schedule
- Redis: scale on list length

### 4. Scale-to-Zero Pattern
- minReplicaCount: 0 in ScaledObject
- Activation threshold: when to wake from zero
- Cold start latency: consider if acceptable for your use case

---

## 🔗 Docs & Resources

- [KEDA docs](https://keda.sh/docs/latest/)
- [KEDA scalers](https://keda.sh/docs/latest/scalers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install KEDA via Helm
- [ ] **Lab 2:** Create an SQS queue, deploy a consumer as Deployment
- [ ] **Lab 3:** Create ScaledObject targeting SQS queue depth (threshold: 10)
- [ ] **Lab 4:** Send 100 messages to SQS — watch pods scale up
- [ ] **Lab 5:** Drain the queue — watch pods scale to zero
- [ ] **Lab 6:** Create a Prometheus scaler for custom app metric

---

## 🐛 Production Issue to Debug
> After labs

- **PI-43:** KEDA ScaledObject not scaling — scaler auth missing, debug TriggerAuthentication

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What problem does KEDA solve that regular HPA cannot?
2. What is the difference between ScaledObject and ScaledJob?
3. How does scale-to-zero work with KEDA?
4. Name 3 event sources KEDA can scale on.
5. What is TriggerAuthentication in KEDA?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-43
- [ ] Answered interview questions
- [ ] Notes written
