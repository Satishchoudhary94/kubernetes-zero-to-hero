# Day 02 — Container Runtimes + CRI

> **Phase:** 0 — Pre-Flight | **Week:** Pre-Week | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Container Runtime Interface (CRI)
- Why CRI exists: decouple kubelet from runtime
- CRI gRPC API: RuntimeService + ImageService
- How kubelet talks to containerd/CRI-O via CRI

### 2. containerd Architecture
- containerd daemon, snapshotter, image store
- runc: the actual low-level OCI runtime
- containerd → runc → container (the call chain)
- containerd config: /etc/containerd/config.toml

### 3. CRI-O
- Lightweight runtime designed specifically for Kubernetes
- CRI-O vs containerd: key differences
- Used by: OpenShift

### 4. crictl — The Node-Level Debug Tool
- crictl replaces docker on Kubernetes nodes
- crictl ps, crictl images, crictl logs, crictl exec
- crictl pods — see pod sandboxes
- crictl config --runtime-endpoint

### 5. Why Docker Was Removed from Kubernetes (v1.24)
- dockershim maintenance burden
- Docker uses containerd internally anyway
- What changed for image builds (nothing) vs node runtime (everything)

---

## 🔗 Docs & Resources

- [containerd docs](https://containerd.io/docs/)
- [CRI-O docs](https://cri-o.io/)
- [crictl usage guide](https://kubernetes.io/docs/tasks/debug/debug-cluster/crictl/)
- [Kubernetes CRI docs](https://kubernetes.io/docs/concepts/architecture/cri/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install crictl and configure it to connect to containerd socket
- [ ] **Lab 2:** Use `crictl ps` to list running containers on a node
- [ ] **Lab 3:** Use `crictl images` to list cached images
- [ ] **Lab 4:** Use `crictl logs <container-id>` to read container logs
- [ ] **Lab 5:** Inspect containerd config at `/etc/containerd/config.toml`
- [ ] **Lab 6:** Trace the full call chain: kubelet → CRI → containerd → runc

---

## 🐛 Production Issue to Debug
> After labs

- **PI-00b:** Pod stuck in ContainerCreating — containerd socket permission issue

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the Container Runtime Interface and why does it exist?
2. What is the difference between containerd and runc?
3. Why was dockershim removed from Kubernetes?
4. How do you debug container issues on a node without docker?
5. What is a pod sandbox (pause container) and why does it exist?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-00b
- [ ] Answered interview questions
- [ ] Notes written
