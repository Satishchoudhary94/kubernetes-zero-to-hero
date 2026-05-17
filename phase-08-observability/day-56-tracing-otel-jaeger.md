# Day 56 — Distributed Tracing — OTEL + Jaeger

> **Phase:** 8 — Observability | **Week:** Week 10 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Why Distributed Tracing
- Logs tell you what happened in one service
- Traces tell you what happened across all services for one request
- Trace: collection of spans (one span per service hop)
- Correlation ID connects spans across services

### 2. OpenTelemetry (OTEL)
- Standard for traces, metrics, and logs
- SDK: instrument your app (Go, Python, Node.js, Java)
- OTEL Collector: receive, process, export telemetry
- Auto-instrumentation: inject OTEL without code changes (OTEL Operator)

### 3. Jaeger
- Distributed tracing backend: stores and visualizes traces
- UI: trace timeline, service dependency graph
- Storage backends: Cassandra, Elasticsearch, Badger (dev)
- Sampling: head-based (probabilistic) vs tail-based (error-based)

### 4. OTEL Operator for Kubernetes
- Auto-inject OTEL agent via annotation
- Instrumentation CRD: configure which SDK and sampling
- No code changes required for auto-instrumentation

---

## 🔗 Docs & Resources

- [OpenTelemetry](https://opentelemetry.io/docs/)
- [Jaeger](https://www.jaegertracing.io/docs/)
- [OTEL Operator](https://opentelemetry.io/docs/kubernetes/operator/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install Jaeger (all-in-one dev mode) on Kubernetes
- [ ] **Lab 2:** Install OTEL Operator
- [ ] **Lab 3:** Deploy 3 microservices (frontend, api, database-mock)
- [ ] **Lab 4:** Create Instrumentation CR for auto-injection
- [ ] **Lab 5:** Annotate services for auto-instrumentation
- [ ] **Lab 6:** Trace a request through all 3 services in Jaeger UI
- [ ] **Lab 7:** Filter traces by error in Jaeger UI

---

## 🐛 Production Issue to Debug
> After labs

- **PI-57:** Traces not appearing in Jaeger — OTEL collector not forwarding, check exporter config

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a trace and a span?
2. What is OpenTelemetry?
3. How does auto-instrumentation work with the OTEL Operator?
4. What is sampling and why is it needed?
5. How do you trace a request across 3 microservices?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-57
- [ ] Answered interview questions
- [ ] Notes written
