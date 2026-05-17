# Day 39 — Image Security + Supply Chain

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Image Security Best Practices
- Never use :latest tag in production — use digest or semver
- Distroless images: no shell, no package manager, minimal attack surface
- Scratch images: completely empty, for statically compiled binaries
- Multi-stage builds: build in full image, copy binary to distroless

### 2. Vulnerability Scanning
- Trivy: fast, accurate, supports images, filesystems, git repos
- Snyk: developer-friendly vulnerability scanning
- Scan in CI: block merge if HIGH/CRITICAL CVEs found
- Scan in registry: ECR has built-in image scanning

### 3. Image Signing with Cosign
- Cosign: sign container images with cryptographic signatures
- Sigstore: public good infrastructure for signing
- Sign after build: cosign sign <image>
- Verify: cosign verify <image>

### 4. Policy Enforcement
- Kyverno policy: only allow signed images
- Kyverno policy: block :latest tag
- Kyverno policy: require images from approved registries only

### 5. RuntimeClass
- Run untrusted workloads in sandboxed runtimes
- gVisor: userspace kernel (strong isolation)
- Kata Containers: lightweight VMs
- RuntimeClass: spec.runtimeClassName in pod spec

---

## 🔗 Docs & Resources

- [Cosign](https://docs.sigstore.dev/cosign/overview/)
- [Trivy](https://trivy.dev/latest/)
- [RuntimeClass](https://kubernetes.io/docs/concepts/containers/runtime-class/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Scan an image with Trivy: `trivy image nginx:latest`
- [ ] **Lab 2:** Build a distroless Go app image
- [ ] **Lab 3:** Sign the image with Cosign (keyless with OIDC)
- [ ] **Lab 4:** Create Kyverno policy to verify image signatures
- [ ] **Lab 5:** Create Kyverno policy to block :latest tag
- [ ] **Lab 6:** Test: try deploying unsigned image — observe policy rejection

---

## 🐛 Production Issue to Debug
> After labs

- **PI-39:** Pod rejected by admission — Kyverno policy denies unsigned image, debug and sign

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why should you not use :latest tag in production?
2. What is a distroless image?
3. What is Cosign and what does image signing prove?
4. How do you enforce image signing using Kyverno?
5. What is RuntimeClass and when would you use gVisor?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-39
- [ ] Answered interview questions
- [ ] Notes written
