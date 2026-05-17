# Day 30 — Secrets — All Types

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Secret Types
- Opaque: generic base64 key-value (most common)
- kubernetes.io/tls: TLS cert + key pair
- kubernetes.io/dockerconfigjson: private registry auth
- kubernetes.io/service-account-token: SA token (legacy)
- kubernetes.io/ssh-auth: SSH private key
- bootstrap.kubernetes.io/token: node bootstrap token

### 2. Secrets Are NOT Encrypted By Default
- Base64 encoding ≠ encryption
- Secrets stored in etcd in plaintext (base64 only)
- Enable encryption at rest: EncryptionConfiguration
- Use Sealed Secrets or External Secrets for real security

### 3. Encryption at Rest
- EncryptionConfiguration: aescbc, aesgcm, kms provider
- KMS provider: integrate with AWS KMS or HashiCorp Vault
- Existing secrets must be rewritten after enabling encryption

### 4. Private Registry Auth (ECR)
- Create Secret of type kubernetes.io/dockerconfigjson
- Reference in pod spec: imagePullSecrets
- EKS: use IRSA instead of storing credentials

---

## 🔗 Docs & Resources

- [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/)
- [Encrypting secret data at rest](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create each secret type and inspect the base64 encoded content
- [ ] **Lab 2:** Mount an Opaque secret as env var and as volume
- [ ] **Lab 3:** Create dockerconfigjson secret for ECR, use in imagePullSecrets
- [ ] **Lab 4:** Enable EncryptionConfiguration for secrets (on kubeadm cluster)
- [ ] **Lab 5:** Verify encryption: read secret directly from etcd — should be encrypted

---

## 🐛 Production Issue to Debug
> After labs

- **PI-29:** ImagePullBackOff — ECR auth secret has wrong format or expired token

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the different Kubernetes Secret types?
2. Why are Kubernetes Secrets not actually secure by default?
3. How do you encrypt Secrets at rest?
4. How do you pull from a private ECR registry in a pod?
5. What is the difference between base64 encoding and encryption?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-29
- [ ] Answered interview questions
- [ ] Notes written
