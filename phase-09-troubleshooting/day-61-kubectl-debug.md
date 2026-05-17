# Day 61 — kubectl debug + Ephemeral Containers

> **Phase:** 9 — Troubleshooting | **Week:** Week 11 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. kubectl debug Modes
- Pod debugging: add ephemeral container to running pod
- Node debugging: privileged pod on the node
- Pod copy debugging: create copy of pod with debug image

### 2. Ephemeral Container Deep Dive
- Injected at runtime into a running pod
- Shares network namespace with pod (can reach localhost)
- targetContainer: share PID namespace to see processes
- Cannot be removed — pod must be deleted
- Use case: debug distroless/scratch images that have no shell

### 3. Pod Copy Debugging
- kubectl debug <pod> --copy-to=<new-pod> --image=<debug-image>
- Creates a new pod with debug image instead of app image
- Good for: test with different config, add debug tools
- Does not affect original pod

### 4. Node Debugging
- kubectl debug node/<name> -it --image=ubuntu
- Creates privileged pod on the node
- chroot /host: access node filesystem
- See node processes: ps aux

---

## 🔗 Docs & Resources

- [kubectl debug](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/)
- [Ephemeral containers](https://kubernetes.io/docs/concepts/workloads/pods/ephemeral-containers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Debug a distroless nginx pod using kubectl debug + ephemeral busybox
- [ ] **Lab 2:** Debug a pod's network using netshoot as ephemeral container with --target
- [ ] **Lab 3:** Create a copy of a broken pod with a debug image
- [ ] **Lab 4:** Debug a node filesystem issue using kubectl debug node
- [ ] **Lab 5:** Inspect node processes from a debug pod with `chroot /host`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-59:** App broken in distroless container — no shell, use ephemeral container to diagnose

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is an ephemeral container?
2. How does `kubectl debug node` work?
3. When would you use `kubectl debug --copy-to` vs ephemeral container?
4. How do you share PID namespace with the target container in debug mode?
5. What is the limitation of ephemeral containers?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-59
- [ ] Answered interview questions
- [ ] Notes written
