# Day 64 — Deployment Strategies

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Rolling Update (Built-in)
- Default Kubernetes strategy
- Gradual replacement: new pods added, old removed
- Zero downtime if readiness probes configured correctly
- Rollback: kubectl rollout undo

### 2. Recreate (Built-in)
- Kill all pods, then create all new
- Downtime: use only for incompatible database migrations

### 3. Blue-Green Deployment
- Two full environments: blue (current) and green (new)
- Switch traffic: update Service selector from blue to green
- Instant rollback: switch selector back
- Cost: 2x resource usage during transition

### 4. Canary Deployment
- Send X% of traffic to new version
- Gradually increase if metrics are healthy
- Implementations: multiple Deployments + Service weights, Ingress, Istio, Argo Rollouts
- Metric gates: automatic rollback if error rate spikes

### 5. Argo Rollouts
- Progressive delivery: automate canary + blue-green
- Analysis templates: PromQL gates for auto-rollback
- Rollout resource: drop-in replacement for Deployment
- Dashboard: visualize rollout progress

---

## 🔗 Docs & Resources

- [Argo Rollouts](https://argoproj.github.io/argo-rollouts/)
- [Deployment strategies](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Implement blue-green: two Deployments, switch Service selector
- [ ] **Lab 2:** Implement canary: 2 Deployments, 90/10 traffic split via NGINX Ingress weights
- [ ] **Lab 3:** Install Argo Rollouts
- [ ] **Lab 4:** Convert a Deployment to Rollout resource with canary strategy
- [ ] **Lab 5:** Create an AnalysisTemplate: if error rate > 1% in Prometheus → auto-rollback
- [ ] **Lab 6:** Trigger a canary that fails the analysis — watch automatic rollback

---

## 🐛 Production Issue to Debug
> After labs

- **PI-62:** Canary rollout not auto-rolling back — AnalysisTemplate query returns no data

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between blue-green and canary?
2. How do you implement canary without Argo Rollouts?
3. What is Argo Rollouts and what problem does it solve?
4. What is an AnalysisTemplate?
5. How does automatic rollback work in Argo Rollouts?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-62
- [ ] Answered interview questions
- [ ] Notes written
