# Day 71 — CKAD — Developer Exam Prep

> **Phase:** 11 — Certification | **Week:** Week 11 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. CKAD vs CKA
- CKAD: 120 min, application-developer focus
- Same pass mark (66%), same simulator (killer.sh)
- Less infra/etcd, more workloads/probes/configmap/secret
- Heavy on multi-container patterns and observability

### 2. Core CKAD Skills
- Pod design: init, sidecar, ambassador, adapter patterns
- ConfigMap/Secret injection (env vs volume vs envFrom)
- Probes: liveness, readiness, startup — when each fires
- Jobs and CronJobs: completion modes, parallelism, restartPolicy
- Service exposure: ClusterIP → NodePort → LoadBalancer → Ingress

### 3. Helm Basics for CKAD
- helm install / upgrade / rollback / uninstall
- values.yaml override with --set or -f
- helm template — render without installing (often a CKAD task)

### 4. Resource Limits & QoS
- Guaranteed: requests==limits for all containers
- Burstable: requests<limits OR limits unset for some
- BestEffort: no requests, no limits
- QoS affects eviction order under node pressure

---

## 🔗 Docs & Resources

- [CNCF CKAD Curriculum](https://github.com/cncf/curriculum)
- [CKAD Exercises](https://github.com/dgkanatsios/CKAD-exercises)
- [Pod Design Patterns](https://kubernetes.io/blog/2016/06/container-design-patterns/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Build a Pod with init container, main app, and logging sidecar
- [ ] **Lab 2:** Inject ConfigMap as env vars AND as a mounted file in one Pod
- [ ] **Lab 3:** Configure liveness + readiness + startup probes that test correctly
- [ ] **Lab 4:** Create a CronJob that runs every 5 min with successfulJobsHistoryLimit=2
- [ ] **Lab 5:** Install nginx via Helm with custom values, then rollback

---

## 🐛 Production Issue to Debug
> After labs

- **PI-CKAD-01:** Liveness probe kills pod every 30s — startup probe missing, slow init.
- **PI-CKAD-02:** ConfigMap update doesn't reflect in pod — envFrom is immutable until restart.

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why does a ConfigMap mounted as a volume update automatically but envFrom doesn't?
2. What's the difference between startupProbe and initialDelaySeconds on livenessProbe?
3. When would you use the ambassador pattern over a regular sidecar?
4. Why is restartPolicy: Never required for some Job patterns?
5. How does QoS class affect pod eviction during node pressure?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-CKAD-01
- [ ] Debugged PI-CKAD-02
- [ ] Answered interview questions
- [ ] Notes written
