# Day 36 — ServiceAccounts + IRSA

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. ServiceAccounts
- Identity for pods (not humans)
- Default SA: created in every namespace automatically
- Token auto-mounted at /var/run/secrets/kubernetes.io/serviceaccount/
- automountServiceAccountToken: false to disable
- Projected SA tokens: short-lived, audience-bound (1.20+)

### 2. IRSA — IAM Role for Service Account (EKS)
- Problem: pods on EC2 get the node's IAM role — too broad
- IRSA: individual pods get individual IAM roles via OIDC
- How it works: OIDC Provider → IAM Trust Policy → AssumeRoleWithWebIdentity
- Setup: annotate ServiceAccount with eks.amazonaws.com/role-arn

### 3. IRSA Setup Steps
- 1. Create OIDC provider for EKS cluster in IAM
- 2. Create IAM role with trust policy referencing SA
- 3. Annotate ServiceAccount with role ARN
- 4. Pod automatically gets AWS credentials via env vars

### 4. Least-Privilege Pattern
- Each microservice gets its own ServiceAccount
- Each SA gets its own IAM role with minimal permissions
- No shared node-level IAM roles for pods

---

## 🔗 Docs & Resources

- [ServiceAccounts](https://kubernetes.io/docs/concepts/security/service-accounts/)
- [IRSA docs](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a ServiceAccount and bind it to a pod
- [ ] **Lab 2:** Verify token is mounted: exec into pod and cat the token file
- [ ] **Lab 3:** Decode the JWT token and read the claims
- [ ] **Lab 4:** Set automountServiceAccountToken: false — verify token not mounted
- [ ] **Lab 5:** On EKS: set up IRSA for S3 read access, verify pod can list S3 buckets
- [ ] **Lab 6:** Verify IRSA: run `aws sts get-caller-identity` from inside the pod

---

## 🐛 Production Issue to Debug
> After labs

- **PI-36:** Pod can't access S3 — IRSA annotation missing or trust policy wrong, debug steps

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is a ServiceAccount and how does it differ from a user?
2. What is IRSA and why is it better than node IAM roles?
3. How does IRSA use OIDC federation?
4. How do you disable ServiceAccount token auto-mounting?
5. What is the principle of least privilege for EKS pods?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-36
- [ ] Answered interview questions
- [ ] Notes written
