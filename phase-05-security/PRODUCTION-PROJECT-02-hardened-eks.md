# Production Project 02 — Hardened EKS Cluster — Security Baseline

> **Type:** Production Project | **Platform:** AWS EKS

---

## 🎯 Goal

Build a production-hardened EKS cluster implementing defense-in-depth: IRSA, Pod Security Admission, Kyverno policies, External Secrets, Network policies, and full audit logging.

---

## 🏗️ Architecture

- EKS cluster with private API endpoint
- IRSA for all service accounts (no node-level IAM for pods)
- Pod Security Admission: restricted on production namespace
- Kyverno: image signing policy + no latest tag + resource limits required
- Network policies: default-deny-all in production namespace
- External Secrets: all secrets from AWS Secrets Manager
- Audit logging: Secret access logs → CloudWatch
- Trivy scanning in CI pipeline

---

## 📋 Build Phases

### Phase 1: Cluster Hardening
- [ ] Create EKS with private endpoint + authorized CIDR
- [ ] Enable envelope encryption for etcd (AWS KMS)
- [ ] Enable EKS control plane logging

### Phase 2: Identity and Access
- [ ] Create unique ServiceAccount per microservice
- [ ] Set up IRSA for each SA with minimal IAM permissions
- [ ] Disable default ServiceAccount token auto-mount cluster-wide

### Phase 3: Pod Security
- [ ] Apply PSA restricted to production namespace
- [ ] Fix all deployment specs to comply with restricted
- [ ] Install Kyverno, create 4 policies: sign, no-latest, limits, approved-registries

### Phase 4: Secrets Management
- [ ] Deploy ESO, create ClusterSecretStore pointing to Secrets Manager
- [ ] Migrate all Secrets to ExternalSecret resources
- [ ] Verify no plaintext secrets exist in cluster

### Phase 5: Network Security
- [ ] Apply default-deny-all NetworkPolicy to production namespace
- [ ] Add explicit allow rules per service
- [ ] Verify inter-service isolation with netshoot

### Phase 6: Audit
- [ ] Configure audit policy: log Secret reads at RequestResponse
- [ ] Send audit logs to CloudWatch
- [ ] Create CloudWatch alarm: alert on >10 secret reads per minute

---

## 🐛 Inject & Debug (after full build)

- [ ] PI-35: Remove a verb from a ServiceAccount role — observe 403, debug RBAC trace
- [ ] PI-36: Break IRSA annotation — pod loses AWS access, debug trust policy
- [ ] PI-37: Upgrade PSA from baseline to restricted — fix failing pods
- [ ] PI-39: Deploy unsigned image — Kyverno blocks it, sign and redeploy
- [ ] PI-40: Simulate cert expiry scenario and recovery steps

---

## ✅ Done When

- [ ] No pod uses node IAM role — all use IRSA
- [ ] All production pods comply with restricted PSA
- [ ] No plaintext secrets in cluster (all from Secrets Manager)
- [ ] Kyverno blocks unsigned images and :latest tags
- [ ] Default-deny NetworkPolicy active in production
- [ ] Audit logs flowing to CloudWatch
- [ ] All 5 injected security issues debugged and resolved
