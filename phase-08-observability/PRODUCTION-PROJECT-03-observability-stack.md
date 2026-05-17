# Production Project 03 — Full Observability Stack on EKS

> **Type:** Production Project | **Platform:** AWS EKS

---

## 🎯 Goal

Build a complete production observability stack on EKS: metrics (Prometheus + Grafana), logs (Fluent Bit → CloudWatch), and traces (OTEL → Jaeger). Deploy a sample microservices app and make it fully observable.

---

## 🏗️ Architecture

- kube-prometheus-stack: Prometheus + Grafana + Alertmanager
- Fluent Bit DaemonSet → CloudWatch Logs
- OTEL Collector DaemonSet
- Jaeger for trace visualization
- Sample app: 3 microservices (frontend, api, worker)
- IRSA for Fluent Bit CloudWatch access
- Slack webhook for alerts

---

## 📋 Build Phases

### Phase 1: Metrics Stack
- [ ] Install kube-prometheus-stack
- [ ] Create ServiceMonitors for all 3 microservices
- [ ] Build Grafana dashboard: RPS, error rate, p99 latency per service
- [ ] Create alert: error rate > 1% for 5 minutes → Slack
- [ ] Create alert: pod restarts > 3 in 10 minutes → Slack

### Phase 2: Logging Stack
- [ ] Deploy Fluent Bit with IRSA (CloudWatch permissions)
- [ ] Configure structured JSON log parsing
- [ ] Create CloudWatch Logs Insights queries for error tracking
- [ ] Set up CloudWatch alarm: >10 errors per minute

### Phase 3: Tracing Stack
- [ ] Install OTEL Operator
- [ ] Create Instrumentation CR
- [ ] Auto-instrument all 3 microservices
- [ ] Deploy Jaeger with Elasticsearch storage
- [ ] Verify end-to-end traces in Jaeger UI

### Phase 4: Validation
- [ ] Inject 5 production issues into the app
- [ ] Find each issue using ONLY observability tools (no kubectl exec)
- [ ] Document: which tool found which issue

---

## 🐛 Inject & Debug (after full build)

- [ ] PI-52: Inject liveness probe that fails under load — find in Grafana restarts graph
- [ ] PI-54: Break Fluent Bit IRSA — find missing logs, restore permissions
- [ ] PI-55: Break ServiceMonitor label — Prometheus stops scraping, find in Grafana
- [ ] PI-57: Break OTEL exporter endpoint — traces missing, debug collector config
- [ ] PI-22: Kill CoreDNS pods — find service call failures in Jaeger traces

---

## ✅ Done When

- [ ] Grafana shows metrics for all services
- [ ] CloudWatch Logs Insights returns app logs
- [ ] Jaeger shows full traces across 3 services
- [ ] All 5 injected issues found using observability tools
- [ ] Slack receives alerts when errors injected
