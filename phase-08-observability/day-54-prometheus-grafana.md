# Day 54 — Prometheus + Grafana on Kubernetes

> **Phase:** 8 — Observability | **Week:** Week 10 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. kube-prometheus-stack
- Helm chart: Prometheus + Grafana + Alertmanager + pre-built dashboards
- Prometheus Operator: manages Prometheus instances as CRDs
- ServiceMonitor: tells Prometheus which services to scrape
- PodMonitor: tells Prometheus which pods to scrape

### 2. Prometheus Data Model
- Metric types: Counter, Gauge, Histogram, Summary
- Labels: dimensions on a metric
- PromQL: Prometheus query language
- Key K8s metrics: container_cpu_usage_seconds_total, kube_pod_status_phase

### 3. Grafana Dashboards
- Pre-built: Kubernetes cluster, nodes, workloads dashboards
- Custom dashboards: PromQL panels
- Variables: dynamic dashboards (select namespace, pod)
- SLO dashboards: error rate, p99 latency, availability

### 4. Alertmanager
- Routes alerts to: Slack, PagerDuty, email, webhook
- Alert rules: PrometheusRule CRD
- Inhibition: suppress child alerts when parent fires
- Silence: suppress alerts for maintenance windows

---

## 🔗 Docs & Resources

- [kube-prometheus-stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)
- [PromQL basics](https://prometheus.io/docs/prometheus/latest/querying/basics/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install kube-prometheus-stack via Helm
- [ ] **Lab 2:** Access Grafana and explore pre-built Kubernetes dashboards
- [ ] **Lab 3:** Write PromQL: CPU usage per pod, memory usage per namespace
- [ ] **Lab 4:** Create a ServiceMonitor for your own app
- [ ] **Lab 5:** Create a PrometheusRule: alert when pod restarts > 3 in 5 minutes
- [ ] **Lab 6:** Configure Alertmanager to send alert to a Slack webhook
- [ ] **Lab 7:** Build a custom Grafana dashboard with 4 panels

---

## 🐛 Production Issue to Debug
> After labs

- **PI-55:** Prometheus not scraping app — ServiceMonitor label mismatch with Prometheus selector

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between Counter and Gauge metrics?
2. What is a ServiceMonitor?
3. How do you write a PromQL query for pod CPU usage?
4. What is AlertManager and how does it route alerts?
5. How do you expose custom metrics from an app for Prometheus?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-55
- [ ] Answered interview questions
- [ ] Notes written
