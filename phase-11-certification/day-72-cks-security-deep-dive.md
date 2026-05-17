# Day 72 — CKS — Security Specialist Exam Prep

> **Phase:** 11 — Certification | **Week:** Week 11 | **Time:** 5–6 hours

---

## 📚 Topics to Study

### 1. CKS Prerequisites
- Must hold valid CKA before taking CKS
- 120 min, 66% pass mark, performance-based
- Heavily focused on practical hardening, not theory

### 2. Domain Coverage
- Cluster Setup — 10% (CIS benchmark, kube-bench)
- Cluster Hardening — 15% (RBAC, ServiceAccounts, kubelet)
- System Hardening — 15% (AppArmor, seccomp, runtime)
- Minimize Microservice Vulnerabilities — 20% (PSS, secrets, sandboxing)
- Supply Chain Security — 20% (image scanning, signing, admission)
- Monitoring, Logging & Runtime Security — 20% (Falco, audit)

### 3. Key Tools to Master
- kube-bench — CIS benchmark scanner
- kube-hunter — penetration test for clusters
- trivy / grype — image vulnerability scanner
- Falco — runtime threat detection
- OPA Gatekeeper / Kyverno — admission policies
- gVisor / kata-containers — sandbox runtimes

### 4. Common CKS Tasks
- Write a NetworkPolicy that denies all egress except DNS
- Configure ImagePolicyWebhook to reject unsigned images
- Apply Pod Security Standard 'restricted' to a namespace
- Enable audit logging and find a specific event in logs
- Restrict a SecurityContext: drop ALL caps, runAsNonRoot, readOnlyRootFilesystem

---

## 🔗 Docs & Resources

- [CNCF CKS Curriculum](https://github.com/cncf/curriculum)
- [CIS Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
- [Falco Docs](https://falco.org/docs/)
- [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Run kube-bench against a cluster and remediate one CRITICAL finding
- [ ] **Lab 2:** Configure Falco to alert when a shell is spawned in a container
- [ ] **Lab 3:** Sign an image with cosign and enforce signature verification via Kyverno
- [ ] **Lab 4:** Apply PSS 'restricted' to a namespace, fix a pod that violates it
- [ ] **Lab 5:** Enable audit logging at Metadata level, filter for failed authentications
- [ ] **Lab 6:** Replace runc with gVisor for a single workload

---

## 🐛 Production Issue to Debug
> After labs

- **PI-CKS-01:** Falco fires but doesn't kill the process — gVisor sandbox required to block.
- **PI-CKS-02:** PSS 'restricted' breaks a working app — needs explicit allow-list with runAsNonRoot.
- **PI-CKS-03:** Trivy scan passes locally but fails in CI — base image SBOM mismatch.

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why does CKS require holding a valid CKA?
2. What's the difference between Pod Security Standards and the deprecated PodSecurityPolicy?
3. How does Falco's userspace detection differ from eBPF-based detection?
4. Why is image signing (cosign) not sufficient on its own without admission enforcement?
5. When would you choose gVisor over kata-containers for sandboxing?
6. How does an admission webhook differ from OPA Gatekeeper conceptually?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-CKS-01
- [ ] Debugged PI-CKS-02
- [ ] Debugged PI-CKS-03
- [ ] Answered interview questions
- [ ] Notes written
