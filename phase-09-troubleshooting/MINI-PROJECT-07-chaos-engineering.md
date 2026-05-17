# Mini Project 07 — Chaos Engineering Lab

> **Type:** Mini Project

---

## 🎯 Goal

Deploy a production-like 3-service application, then use Chaos Mesh to inject failures. Find each failure using observability tools and write runbooks.

---

## 🛠️ Stack

- Chaos Mesh
- Prometheus + Grafana
- Fluent Bit
- Jaeger
- netshoot
- k6

---

## 📋 Tasks

- [ ] Deploy 3 microservices: api-gateway, auth-service, data-service
- [ ] Set up full observability (Prometheus, Grafana, Fluent Bit, Jaeger)
- [ ] Install Chaos Mesh
- [ ] Run baseline load test (k6) — capture normal metrics
- [ ] Inject pod-kill chaos on auth-service — find via Grafana error rate spike
- [ ] Inject CPU stress on data-service — find via Grafana CPU dashboard
- [ ] Inject network partition (block auth→data communication) — find via Jaeger traces
- [ ] Inject DNS failure — find via pod logs in CloudWatch
- [ ] Inject memory hog — find via Grafana memory dashboard, see OOMKill
- [ ] Write a runbook for each failure type
- [ ] Implement fixes: PDB, HPA, circuit breakers

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Kill all Prometheus pods mid-chaos — now you're blind, find issues from logs only
- [ ] Inject two simultaneous failures — triage priority order

---

## ✅ Done When

- [ ] Successfully identified all 5 chaos scenarios using observability tools
- [ ] Runbooks written for each failure type
- [ ] PDB added to prevent zero-replica situations
- [ ] App recovers automatically after chaos stopped
- [ ] Both bonus challenge scenarios handled
