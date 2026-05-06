# Mini Project 03 — Complete Application Workload Stack

> **Type:** Mini Project

---

## 🎯 Goal

Build a full application stack using every workload type. Frontend, backend, cache, worker, job, and cron all running together.

---

## 🛠️ Stack

- kubectl
- kind cluster
- Deployment
- StatefulSet
- DaemonSet
- Job
- CronJob

---

## 📋 Tasks

- [ ] Deploy frontend (Nginx) as Deployment with 3 replicas
- [ ] Deploy backend (Node.js) as Deployment with rolling update config
- [ ] Deploy Redis as StatefulSet with 3 pods + headless service
- [ ] Deploy Fluent Bit as DaemonSet for log collection
- [ ] Create a db-migration Job (runs once at deploy time)
- [ ] Create a nightly-report CronJob (every night at 00:00)
- [ ] Scale the backend Deployment to 5 replicas
- [ ] Perform a rolling update on backend with maxSurge=1 maxUnavailable=0
- [ ] Roll back the backend to previous version

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Delete a Redis StatefulSet pod — verify ordered replacement
- [ ] Break the CronJob schedule — observe missed runs
- [ ] Force fail the migration Job — observe backoffLimit behavior

---

## ✅ Done When

- [ ] All workload types running and healthy
- [ ] Rolling update completed and rollback tested
- [ ] StatefulSet pods have stable identities
- [ ] DaemonSet has one pod per node
- [ ] Job completed successfully
- [ ] CronJob has run at least twice
