# Day 52 — Probes — Liveness, Readiness, Startup

> **Phase:** 8 — Observability | **Week:** Week 10 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Probe Types
- Liveness: is the app healthy? Kill and restart if not
- Readiness: is the app ready to serve traffic? Remove from Service if not
- Startup: is the app done starting? Disables liveness until startup completes

### 2. Probe Methods
- HTTP GET: check endpoint returns 2xx/3xx
- TCP Socket: check port is open
- Exec: run a command, success = exit 0
- gRPC: check gRPC health protocol (K8s 1.24+)

### 3. Probe Timing Parameters
- initialDelaySeconds: wait before first probe
- periodSeconds: how often to probe
- timeoutSeconds: probe timeout
- successThreshold: consecutive successes to become Ready
- failureThreshold: consecutive failures before action

### 4. Common Mistakes
- Liveness too aggressive: app restarts under load (false positives)
- No startup probe: slow-starting apps fail liveness immediately
- No readiness probe: traffic sent to not-ready pods
- Same endpoint for liveness and readiness: may not be correct

---

## 🔗 Docs & Resources

- [Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a pod with HTTP liveness, readiness, and startup probes
- [ ] **Lab 2:** Simulate liveness failure: exec into pod and break the health endpoint
- [ ] **Lab 3:** Simulate readiness failure: observe pod removed from Service endpoints
- [ ] **Lab 4:** Use startup probe for a slow-starting app (initialDelaySeconds abuse vs startup probe)
- [ ] **Lab 5:** Tune probes: observe the difference between aggressive vs conservative settings

---

## 🐛 Production Issue to Debug
> After labs

- **PI-52:** Pod restart loop — liveness probe too aggressive, triggering on slow GC pause
- **PI-53:** Traffic going to not-ready pods — readiness probe not configured, add it

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between liveness and readiness probes?
2. When should you use a startup probe?
3. What happens when a readiness probe fails?
4. What happens when a liveness probe fails?
5. What are the 4 probe methods?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-52
- [ ] Debugged PI-53
- [ ] Answered interview questions
- [ ] Notes written
