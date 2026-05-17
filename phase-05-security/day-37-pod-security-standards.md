# Day 37 — Pod Security Standards + PSA

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. PodSecurityPolicy is Gone (K8s 1.25)
- PSP was deprecated in 1.21, removed in 1.25
- Replacement: Pod Security Admission (built-in) + Kyverno/OPA

### 2. Pod Security Standards (PSS)
- Privileged: no restrictions (system workloads)
- Baseline: minimal restrictions, prevents privilege escalation
- Restricted: hardened, best practice security (deny most privileges)

### 3. Pod Security Admission (PSA)
- Built-in admission controller (K8s 1.23+ stable 1.25)
- Namespace labels control which profile to enforce
- Modes: enforce (reject), warn (warn only), audit (log only)
- Labels: pod-security.kubernetes.io/enforce: restricted

### 4. External Policy Engines
- Kyverno: Kubernetes-native, YAML policies
- OPA Gatekeeper: Rego-based policies
- Comparison: Kyverno easier, OPA more powerful
- Common policies: no latest tag, no root user, require labels

---

## 🔗 Docs & Resources

- [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/)
- [Pod Security Admission](https://kubernetes.io/docs/concepts/security/pod-security-admission/)
- [Kyverno](https://kyverno.io/docs/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Label namespace with PSA restricted — deploy an app, observe failures
- [ ] **Lab 2:** Fix the pod spec to comply with restricted policy
- [ ] **Lab 3:** Install Kyverno
- [ ] **Lab 4:** Create Kyverno policy: deny images without digest
- [ ] **Lab 5:** Create Kyverno policy: require all pods to have resource limits
- [ ] **Lab 6:** Test both policies with compliant and non-compliant pods

---

## 🐛 Production Issue to Debug
> After labs

- **PI-37:** Deployment failing after namespace PSA upgrade — pod spec violates restricted policy

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the three Pod Security Standard profiles?
2. What replaced PodSecurityPolicy in Kubernetes 1.25?
3. What are the three PSA modes (enforce, warn, audit)?
4. What is the difference between Kyverno and OPA Gatekeeper?
5. How do you gradually migrate to restricted PSA?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-37
- [ ] Answered interview questions
- [ ] Notes written
