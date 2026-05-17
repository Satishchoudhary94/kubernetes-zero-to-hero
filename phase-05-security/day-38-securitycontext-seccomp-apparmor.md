# Day 38 — SecurityContext + seccomp + AppArmor

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. SecurityContext at Pod and Container Level
- runAsUser / runAsGroup: UID/GID for the process
- fsGroup: GID for volumes — files owned by this group
- runAsNonRoot: reject if image runs as root
- readOnlyRootFilesystem: prevent writes to container FS
- allowPrivilegeEscalation: block setuid, sudo inside container

### 2. Linux Capabilities
- Drop ALL capabilities then add back only what's needed
- Common needed: NET_BIND_SERVICE (bind port <1024)
- Never give: SYS_ADMIN, NET_ADMIN, SYS_PTRACE (too powerful)
- capabilities.drop: [ALL] + capabilities.add: [NET_BIND_SERVICE]

### 3. seccomp Profiles
- Filters system calls a container can make
- RuntimeDefault: kernel-provided safe default profile
- Localhost: custom profile from node filesystem
- Unconfined: no filtering (default, not recommended for prod)
- seccompProfile.type: RuntimeDefault (best practice)

### 4. AppArmor
- Linux MAC (Mandatory Access Control) system
- Restricts file access, network, capabilities per process
- Profile loaded on node, referenced in pod annotation
- container.apparmor.security.beta.kubernetes.io/<container>: runtime/default

---

## 🔗 Docs & Resources

- [SecurityContext](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
- [seccomp](https://kubernetes.io/docs/tutorials/security/seccomp/)
- [AppArmor](https://kubernetes.io/docs/tutorials/security/apparmor/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Harden a pod step by step: add runAsNonRoot, readOnlyRootFilesystem, drop ALL caps
- [ ] **Lab 2:** Verify the hardened pod still works correctly
- [ ] **Lab 3:** Add seccompProfile: RuntimeDefault — verify app still runs
- [ ] **Lab 4:** Create a custom seccomp profile that blocks mkdir syscall
- [ ] **Lab 5:** Apply AppArmor runtime/default profile to a container
- [ ] **Lab 6:** Try to escalate privileges inside a hardened container — observe failure

---

## 🐛 Production Issue to Debug
> After labs

- **PI-38:** App crashes after seccomp profile applied — blocked syscall, identify with strace

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between pod-level and container-level SecurityContext?
2. What does readOnlyRootFilesystem do and when might it break an app?
3. What is a seccomp profile?
4. What is the difference between seccomp RuntimeDefault and Unconfined?
5. How does AppArmor work differently from seccomp?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-38
- [ ] Answered interview questions
- [ ] Notes written
