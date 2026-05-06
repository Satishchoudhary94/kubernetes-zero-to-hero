# Day 25 — cert-manager — Automatic TLS

> **Phase:** 3 — Networking | **Week:** Week 5 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. cert-manager Architecture
- Manages TLS certificates as Kubernetes resources
- Custom resources: Certificate, CertificateRequest, Issuer, ClusterIssuer
- Automatically renews certificates before expiry

### 2. Issuers
- Issuer: namespace-scoped
- ClusterIssuer: cluster-wide
- ACME: Let's Encrypt (HTTP-01 and DNS-01 challenges)
- Self-signed: for internal/dev clusters
- CA: use your own CA cert
- Vault: HashiCorp Vault PKI

### 3. ACME Challenges
- HTTP-01: cert-manager creates /.well-known/acme-challenge/ endpoint
- DNS-01: cert-manager creates TXT record in DNS (Route53)
- DNS-01 required for wildcard certs

### 4. Integration with Ingress
- Annotation: cert-manager.io/cluster-issuer: letsencrypt-prod
- cert-manager auto-creates Certificate object
- TLS secret auto-created and injected into Ingress

---

## 🔗 Docs & Resources

- [cert-manager docs](https://cert-manager.io/docs/)
- [Let's Encrypt](https://letsencrypt.org/docs/)
- [ACME challenge types](https://cert-manager.io/docs/configuration/acme/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install cert-manager via Helm
- [ ] **Lab 2:** Create a self-signed ClusterIssuer
- [ ] **Lab 3:** Create a Certificate resource and verify the TLS secret is created
- [ ] **Lab 4:** Annotate an Ingress with ClusterIssuer — verify auto-cert creation
- [ ] **Lab 5:** Check certificate status: `kubectl describe certificate <name>`
- [ ] **Lab 6:** Simulate cert expiry: check renewal mechanism

---

## 🐛 Production Issue to Debug
> After labs

- **PI-24:** Certificate stuck in NotReady — ACME challenge failing, diagnose cert-manager logs

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What does cert-manager do?
2. What is the difference between Issuer and ClusterIssuer?
3. What is an ACME challenge and what are the two types?
4. Why is DNS-01 required for wildcard certificates?
5. How does cert-manager integrate with Ingress?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-24
- [ ] Answered interview questions
- [ ] Notes written
