# Day 01 — Containers vs VMs

> **Phase:** 0 — Pre-Flight | **Week:** Pre-Week | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Virtual Machines
- Hypervisor types: Type 1 (bare-metal) vs Type 2 (hosted)
- Hardware virtualization — each VM gets a full OS kernel
- Resource overhead: memory, disk, CPU per VM
- Boot time: 30–60 seconds typical

### 2. Linux Containers — Under the Hood
- Linux namespaces: pid, net, mnt, uts, ipc, user
- cgroups v1 vs v2: CPU, memory, blkio limits
- Union filesystem: overlay2, layers, copy-on-write
- OCI image spec and runtime spec

### 3. Containers vs VMs — Direct Comparison
- Startup time | Isolation level | Resource usage
- Security boundary differences
- Use cases: when to choose VM vs container

### 4. Why Containers Alone Are Not Enough at Scale
- No self-healing (crash = gone)
- No auto-scaling
- No built-in service discovery
- Manual networking between hosts
- This is the gap Kubernetes fills

---

## 🔗 Docs & Resources

- [Linux namespaces (man7.org)](https://man7.org/linux/man-pages/man7/namespaces.7.html)
- [cgroups overview (kernel.org)](https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v2.html)
- [OCI Image Spec](https://github.com/opencontainers/image-spec)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Run a container and inspect its namespaces with `lsns` and `/proc/PID/ns`
- [ ] **Lab 2:** Create an isolated process using `unshare --pid --fork --mount-proc bash`
- [ ] **Lab 3:** Inspect cgroup limits of a running container via `/sys/fs/cgroup`
- [ ] **Lab 4:** Measure and compare startup time: VM boot vs `docker run` (use `time`)
- [ ] **Lab 5:** Pull an image and inspect its layers using `dive` tool

---

## 🐛 Production Issue to Debug
> After labs

- **PI-00:** Container consuming 100% CPU — identify using cgroups stats + crictl

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a container and a VM at the kernel level?
2. Which Linux kernel features make containers possible?
3. What is a cgroup and what does it control?
4. What is a union filesystem and why do containers use it?
5. Why can't you just use Docker alone for production at scale?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-00
- [ ] Answered interview questions
- [ ] Notes written
