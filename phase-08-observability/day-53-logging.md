# Day 53 — Logging Architecture

> **Phase:** 8 — Observability | **Week:** Week 10 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Kubernetes Logging Patterns
- Node-level: kubelet manages container logs, rotates them
- App-level: write to stdout/stderr — Kubernetes captures automatically
- Sidecar: log collector sidecar writes to shared volume or direct to backend
- kubectl logs: reads from node-level log files

### 2. Cluster-Level Logging Stack
- Fluent Bit (lightweight) or Fluentd (heavier) as DaemonSet
- Fluent Bit reads node log files → parses → ships to destination
- Destinations: CloudWatch, Elasticsearch, Loki, Splunk
- EKS: Fluent Bit → CloudWatch Logs (AWS managed add-on available)

### 3. Structured Logging Best Practices
- Log as JSON: enables log queries and filtering
- Include: timestamp, level, message, correlation-id, pod-name
- Correlation ID: trace a request through multiple services
- Log levels: use ERROR sparingly, INFO for key events, DEBUG for dev

### 4. CloudWatch Container Insights (EKS)
- Fluent Bit add-on: streams logs to CloudWatch
- Log groups: /aws/containerinsights/<cluster>/application
- CloudWatch Logs Insights: SQL-like queries on logs
- Container Insights: pre-built dashboards for EKS metrics+logs

---

## 🔗 Docs & Resources

- [Logging architecture](https://kubernetes.io/docs/concepts/cluster-administration/logging/)
- [Fluent Bit EKS add-on](https://docs.aws.amazon.com/eks/latest/userguide/fargate-logging.html)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy Fluent Bit as DaemonSet, configure to ship to CloudWatch
- [ ] **Lab 2:** Write a structured JSON log from an app pod
- [ ] **Lab 3:** Query logs in CloudWatch Logs Insights
- [ ] **Lab 4:** Configure Fluent Bit filter to add pod_name to all log records
- [ ] **Lab 5:** Test log rotation: fill disk with logs, verify rotation works

---

## 🐛 Production Issue to Debug
> After labs

- **PI-54:** Logs not appearing in CloudWatch — Fluent Bit IRSA missing CloudWatch permissions

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the 3 Kubernetes logging patterns?
2. Why should applications log to stdout/stderr?
3. What is Fluent Bit and how does it work?
4. What is structured logging and why is it important?
5. How do you query Kubernetes application logs in CloudWatch?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-54
- [ ] Answered interview questions
- [ ] Notes written
