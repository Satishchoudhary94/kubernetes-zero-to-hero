# Day 09 — Init Containers + Sidecar Pattern

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Init Containers
- Run sequentially before app containers start
- Each must complete successfully before next starts
- Use cases: wait for DB, clone git repo, set permissions
- Have same spec as regular containers but different semantics
- Pod phase during init: Init:0/N

### 2. Sidecar Containers (Classic Pattern)
- Runs alongside main container in same pod
- Shares lifecycle with main container
- Use cases: log collector, metrics exporter, service mesh proxy
- Communicates via localhost or shared volumes

### 3. Native Sidecar Containers (K8s 1.29+)
- New: sidecar declared as initContainer with restartPolicy: Always
- Starts before main container, restarts independently
- Survives main container restarts
- Better lifecycle management than classic sidecar

### 4. Ambassador + Adapter Patterns
- Ambassador: proxy external connections (e.g., Redis Twemproxy)
- Adapter: normalize output format (e.g., transform logs to JSON)

---

## 🔗 Docs & Resources

- [Init containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/)
- [Sidecar containers (1.29+)](https://kubernetes.io/docs/concepts/workloads/pods/sidecar-containers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a pod with an init container that waits for a service to be available
- [ ] **Lab 2:** Create a pod where init container writes a config file, main container reads it
- [ ] **Lab 3:** Build a pod with a Fluent Bit sidecar collecting logs from main container
- [ ] **Lab 4:** Simulate init container failure and observe pod stuck in Init state
- [ ] **Lab 5:** Use native sidecar syntax (K8s 1.29+) and observe restart behavior difference

---

## 🐛 Production Issue to Debug
> After labs

- **PI-07:** Pod stuck in Init:0/1 — init container failing, how to debug and identify root cause

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the execution order of init containers?
2. What happens if an init container fails?
3. What is the difference between a classic sidecar and a native sidecar (1.29+)?
4. When would you use an Ambassador container?
5. How does a sidecar container access logs from the main container?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-07
- [ ] Answered interview questions
- [ ] Notes written
