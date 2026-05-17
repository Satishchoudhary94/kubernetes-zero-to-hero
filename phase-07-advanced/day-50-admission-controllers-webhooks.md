# Day 50 — Admission Controllers + Webhooks

> **Phase:** 7 — Advanced | **Week:** Week 9 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Built-in Admission Controllers
- ResourceQuota: enforce namespace quotas
- LimitRanger: enforce LimitRange defaults
- NamespaceLifecycle: prevent resources in terminating namespaces
- DefaultStorageClass: inject default storage class
- Enable/disable: --enable-admission-plugins flag on API server

### 2. MutatingAdmissionWebhook
- Called during admission — can modify the request object
- Use cases: inject sidecar, add default labels, set image pull policy
- Webhook server: HTTPS, receives AdmissionReview, returns patch
- TLS required: cert-manager can provision cert

### 3. ValidatingAdmissionWebhook
- Called after mutation — can reject the request
- Cannot modify the object
- Use cases: policy enforcement, custom validation
- Return allowed: false with reason to reject

### 4. Validating Admission Policies (CEL)
- K8s 1.28+ stable: inline CEL policies (no webhook server needed)
- ValidatingAdmissionPolicy + ValidatingAdmissionPolicyBinding
- Much simpler than webhook for simple checks

### 5. Webhook Failure Policy
- Fail: reject request if webhook unreachable (safe but fragile)
- Ignore: allow request if webhook unreachable (risky but resilient)
- timeoutSeconds: how long to wait for webhook

---

## 🔗 Docs & Resources

- [Admission controllers](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/)
- [Webhooks](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/)
- [Validating Admission Policy](https://kubernetes.io/docs/reference/access-authn-authz/validating-admission-policy/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Write a mutating webhook that injects `env: production` label to all pods
- [ ] **Lab 2:** Deploy webhook server with cert-manager TLS cert
- [ ] **Lab 3:** Write a validating webhook that rejects pods without resource limits
- [ ] **Lab 4:** Test both webhooks with compliant and non-compliant pods
- [ ] **Lab 5:** Write a ValidatingAdmissionPolicy using CEL (no webhook server)
- [ ] **Lab 6:** Simulate webhook timeout: observe Fail vs Ignore policy behavior

---

## 🐛 Production Issue to Debug
> After labs

- **PI-50:** All pod creation blocked — mutating webhook timeout with Fail policy, disable webhook to recover

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between mutating and validating webhooks?
2. What is the admission controller request pipeline order?
3. What is a ValidatingAdmissionPolicy and how does it differ from a webhook?
4. What does failurePolicy: Fail mean for a webhook?
5. How do you secure a webhook endpoint?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-50
- [ ] Answered interview questions
- [ ] Notes written
