# Day 12 — Pod Lifecycle + Ephemeral Containers

> **Phase:** 1 — Foundation | **Week:** Week 2 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Pod Phases
- Pending: accepted, waiting for scheduling/image pull
- Running: at least one container running
- Succeeded: all containers exited 0 (Job pods)
- Failed: at least one container exited non-0
- Unknown: node communication lost

### 2. Pod Conditions
- PodScheduled: assigned to a node
- Initialized: all init containers done
- ContainersReady: all containers ready
- Ready: pod can serve traffic (readiness probe passed)

### 3. Container States + Exit Codes
- Waiting, Running, Terminated
- Exit code 0: success | 1: app error | 137: OOMKilled | 139: segfault
- CrashLoopBackOff: repeated failures with backoff
- terminationMessagePath: how Kubernetes captures exit reason

### 4. Pod Termination Lifecycle
- SIGTERM → grace period → SIGKILL
- terminationGracePeriodSeconds (default 30)
- preStop hook: run before SIGTERM
- Why you need graceful shutdown in your app

### 5. Ephemeral Containers
- Temporary containers added to running pods for debugging
- Cannot be removed once added (pod must be deleted)
- Use case: debug distroless or scratch images
- kubectl debug -it <pod> --image=busybox --target=<container>

---

## 🔗 Docs & Resources

- [Pod lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/)
- [Ephemeral containers](https://kubernetes.io/docs/concepts/workloads/pods/ephemeral-containers/)
- [Init containers lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Observe each pod phase by creating pods with different configurations
- [ ] **Lab 2:** Trigger OOMKill and observe exit code 137
- [ ] **Lab 3:** Add a preStop hook and verify it runs before SIGTERM
- [ ] **Lab 4:** Use `kubectl debug` to add ephemeral container to a running nginx pod
- [ ] **Lab 5:** Debug a distroless container using an ephemeral busybox container
- [ ] **Lab 6:** Observe CrashLoopBackOff: create a pod with a bad command, watch backoff timing

---

## 🐛 Production Issue to Debug
> After labs

- **PI-10:** Pod stuck in Terminating — finalizer not releasing, how to force-remove safely
- **PI-11:** CrashLoopBackOff — 5 different root causes and how to diagnose each

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the 5 pod phases and what does each mean?
2. What is the difference between pod phase and pod conditions?
3. What do exit codes 137 and 139 indicate?
4. What is CrashLoopBackOff and how does the backoff timing work?
5. When would you use an ephemeral container?
6. How does terminationGracePeriodSeconds work with preStop hooks?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-10
- [ ] Debugged PI-11
- [ ] Answered interview questions
- [ ] Notes written
