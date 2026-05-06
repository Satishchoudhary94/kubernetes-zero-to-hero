# Day 18 — Jobs + CronJobs

> **Phase:** 2 — Workloads | **Week:** Week 3 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Jobs
- Run-to-completion workloads (not long-running services)
- completions: how many times to run successfully
- parallelism: how many pods to run simultaneously
- backoffLimit: max retries before marking Job failed
- activeDeadlineSeconds: timeout for the entire job
- Job patterns: single, indexed, work queue

### 2. CronJobs
- Creates Jobs on a schedule (Unix cron syntax)
- concurrencyPolicy: Allow, Forbid, Replace
- startingDeadlineSeconds: how late a missed job can start
- successfulJobsHistoryLimit / failedJobsHistoryLimit
- Time zone support: .spec.timeZone (K8s 1.27+)

### 3. Job Patterns
- Single completion: database migration, batch import
- Indexed: parallel processing with task ID per pod
- Work queue: pods pull work from a queue (RabbitMQ, SQS)

---

## 🔗 Docs & Resources

- [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/)
- [CronJob](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/)
- [Job patterns](https://kubernetes.io/docs/tasks/job/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a Job that runs a database migration script (simulate with echo)
- [ ] **Lab 2:** Create a parallel Job with completions=6, parallelism=2
- [ ] **Lab 3:** Create a CronJob that runs every minute and logs a timestamp
- [ ] **Lab 4:** Test concurrencyPolicy: Forbid by making the job run longer than its interval
- [ ] **Lab 5:** Trigger a CronJob manually: `kubectl create job --from=cronjob/<name>`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-17:** CronJob not firing at expected time — timezone misconfiguration

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a Job and a Deployment?
2. What does backoffLimit control in a Job?
3. What is the difference between concurrencyPolicy Allow, Forbid, and Replace?
4. How would you run a database migration safely as a Kubernetes Job?
5. What happens to completed Job pods?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-17
- [ ] Answered interview questions
- [ ] Notes written
