# Day 40 — Audit Logs + OIDC + Kubernetes PKI

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Kubernetes Audit Logging
- Records every API server request with: who, what, when, from where
- Audit policy: defines what to log (levels: None, Metadata, Request, RequestResponse)
- Audit stages: RequestReceived, ResponseStarted, ResponseComplete, Panic
- Backend: log file or webhook (send to SIEM/CloudWatch)
- CKA: configure audit policy file, enable on API server

### 2. OIDC Integration
- Kubernetes supports OIDC as authentication method
- AWS SSO / Okta / GitHub as identity providers
- OIDC token validated by API server
- EKS: aws eks get-token — AWS CLI generates OIDC token for kubectl
- IRSA uses OIDC for pod identity (covered Day 36)

### 3. Kubernetes PKI
- Every cluster has its own CA (Certificate Authority)
- Components authenticated with: certs signed by cluster CA
- Key certs: api-server, etcd, kubelet, front-proxy
- Certificate locations: /etc/kubernetes/pki/
- Check expiry: kubeadm certs check-expiration
- Renew: kubeadm certs renew all

### 4. Certificate Rotation
- kubelet rotates its own cert automatically (RotateKubeletClientCertificate)
- Control plane certs: 1 year expiry by default
- Cluster upgrades renew certs automatically
- Manual rotation for emergency: kubeadm certs renew

---

## 🔗 Docs & Resources

- [Audit logging](https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/)
- [PKI certificates](https://kubernetes.io/docs/setup/best-practices/certificates/)
- [Certificate management](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create an audit policy that logs all Secret access at RequestResponse level
- [ ] **Lab 2:** Enable audit logging on the API server (edit static pod manifest)
- [ ] **Lab 3:** Generate some secret reads and find them in the audit log
- [ ] **Lab 4:** Check certificate expiry: `kubeadm certs check-expiration`
- [ ] **Lab 5:** Renew all certificates: `kubeadm certs renew all`
- [ ] **Lab 6:** Simulate expired cert scenario and recovery

---

## 🐛 Production Issue to Debug
> After labs

- **PI-40:** Cluster access broken after 1 year — all certs expired, recovery procedure

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the purpose of Kubernetes audit logs?
2. What are the 4 audit log levels?
3. How does OIDC authentication work in Kubernetes?
4. Where are Kubernetes PKI certificates stored?
5. How do you renew Kubernetes certificates before they expire?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-40
- [ ] Answered interview questions
- [ ] Notes written
