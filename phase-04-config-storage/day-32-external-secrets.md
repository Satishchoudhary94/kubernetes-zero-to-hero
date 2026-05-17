# Day 32 — External Secrets — Vault + ESO

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. The Problem with Native Secrets
- Secrets in Git = security breach
- Base64 in etcd = not encrypted by default
- Manual rotation = operational burden

### 2. External Secrets Operator (ESO)
- Syncs secrets from external stores into Kubernetes Secrets
- SecretStore: connection config to external system
- ClusterSecretStore: cluster-wide secret store
- ExternalSecret: what to fetch and where to put it
- Auto-refresh: re-syncs on a schedule

### 3. AWS Secrets Manager + SSM Parameter Store
- SecretStore with AWS provider + IRSA for auth
- ExternalSecret references secret ARN or path
- Auto-rotation: rotate in Secrets Manager → K8s secret auto-updates

### 4. HashiCorp Vault Integration
- Vault: enterprise-grade secret management
- Auth methods: Kubernetes auth (uses SA token)
- ESO Vault provider: SecretStore points to Vault endpoint
- Dynamic secrets: Vault generates DB credentials on demand

---

## 🔗 Docs & Resources

- [External Secrets Operator](https://external-secrets.io/latest/)
- [AWS Secrets Manager provider](https://external-secrets.io/latest/provider/aws-secrets-manager/)
- [HashiCorp Vault](https://developer.hashicorp.com/vault/docs/auth/kubernetes)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install External Secrets Operator via Helm
- [ ] **Lab 2:** Create a secret in AWS Secrets Manager
- [ ] **Lab 3:** Create SecretStore with AWS provider (IRSA) + ExternalSecret
- [ ] **Lab 4:** Verify Kubernetes Secret created from AWS Secrets Manager value
- [ ] **Lab 5:** Update the secret in AWS — verify K8s secret auto-updates
- [ ] **Lab 6:** Deploy HashiCorp Vault (dev mode) and integrate with ESO

---

## 🐛 Production Issue to Debug
> After labs

- **PI-31:** ExternalSecret stuck in SecretSyncedError — IRSA policy missing required permission

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why should you not store secrets in git?
2. What does External Secrets Operator do?
3. What is the difference between SecretStore and ClusterSecretStore?
4. How does ESO authenticate with AWS Secrets Manager on EKS?
5. What are Vault dynamic secrets?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-31
- [ ] Answered interview questions
- [ ] Notes written
