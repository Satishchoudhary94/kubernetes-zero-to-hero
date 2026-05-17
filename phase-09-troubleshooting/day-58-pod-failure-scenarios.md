# Day 58 — Pod Failure Scenarios

> **Phase:** 9 — Troubleshooting | **Week:** Week 11 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. CrashLoopBackOff — 5 Root Causes
- 1. App exits immediately — bad entrypoint or missing config
- 2. OOMKilled — memory limit too low
- 3. Liveness probe killing healthy app — tune probe
- 4. Missing dependency — database not ready (use init container)
- 5. Permission error — readOnlyRootFilesystem + writing to FS

### 2. OOMKilled
- Exit code 137: process killed by OOM killer
- kubectl describe pod: OOMKilled in lastState
- Fix: increase memory limit OR fix memory leak in app
- VPA: use recommendations to right-size

### 3. ImagePullBackOff
- Image doesn't exist or wrong tag
- Private registry: missing imagePullSecret
- ECR: token expired or IRSA misconfigured
- Network: can node reach registry?

### 4. Pod Stuck in Terminating
- Finalizer not released by controller
- Force delete: kubectl delete pod --grace-period=0 --force (use carefully)
- Root cause: controller crashed while object has finalizer

### 5. RunContainerError
- Volume mount failure: PVC not bound, wrong path
- Init container not completed
- SecurityContext violation (readOnly + write attempt)

---

## 🔗 Docs & Resources

- [Debug running pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/)
- [Debug init containers](https://kubernetes.io/docs/tasks/debug/debug-application/debug-init-containers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy a pod with each failure type, debug and fix each one
- [ ] **Lab 2:** CrashLoopBackOff lab: app exits on missing env var
- [ ] **Lab 3:** OOMKilled lab: app with memory leak, diagnose and set correct limit
- [ ] **Lab 4:** ImagePullBackOff lab: wrong image tag, then fix
- [ ] **Lab 5:** Stuck Terminating lab: add finalizer manually, then remove to unstick
- [ ] **Lab 6:** RunContainerError lab: wrong volume mount path

---

## 🐛 Production Issue to Debug
> After labs

- **PI-06:** OOMKilled — find the memory limit, identify leak, set correct value
- **PI-10:** Pod stuck in Terminating — force delete decision and consequences
- **PI-11:** CrashLoopBackOff — identify which of 5 causes applies

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the 5 most common causes of CrashLoopBackOff?
2. What is exit code 137 and what causes it?
3. How do you debug a pod that crashes immediately on start?
4. When is it safe to force-delete a pod?
5. How do you debug an ImagePullBackOff for a private ECR image?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-06
- [ ] Debugged PI-10
- [ ] Debugged PI-11
- [ ] Answered interview questions
- [ ] Notes written
