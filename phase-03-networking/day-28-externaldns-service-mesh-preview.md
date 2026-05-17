# Day 28 — ExternalDNS + Service Mesh Preview

> **Phase:** 3 — Networking | **Week:** Week 5 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. ExternalDNS
- Automatically syncs Kubernetes Services/Ingress to DNS providers
- Supports: Route53, Cloudflare, GCP DNS, Azure DNS
- Watches Service with type=LoadBalancer → creates A record in Route53
- Watches Ingress hosts → creates CNAME/A record
- Annotations to control behavior: external-dns.alpha.kubernetes.io/hostname

### 2. ExternalDNS on EKS
- Uses IRSA for Route53 permissions
- IAM policy: route53:ChangeResourceRecordSets
- Deployed as Deployment in kube-system

### 3. Service Mesh — Why It Exists
- Microservices need: mTLS, retries, circuit breaking, observability
- Implementing these in each service = code duplication
- Service mesh: move these concerns to infrastructure layer
- Envoy sidecar injected automatically

### 4. Istio Preview (full coverage on Day 65)
- Control plane: istiod
- Data plane: Envoy sidecar proxies
- mTLS: automatic mutual TLS between services
- Traffic management: VirtualService, DestinationRule

---

## 🔗 Docs & Resources

- [ExternalDNS](https://kubernetes-sigs.github.io/external-dns/)
- [Istio intro](https://istio.io/latest/docs/concepts/what-is-istio/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Deploy ExternalDNS with Route53 provider (use IRSA on EKS)
- [ ] **Lab 2:** Create a LoadBalancer service — verify DNS record auto-created in Route53
- [ ] **Lab 3:** Create an Ingress with a hostname — verify CNAME auto-created
- [ ] **Lab 4:** Read: Istio architecture overview (prep for Day 65)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-27:** ExternalDNS not creating records — IRSA permissions missing, debug IAM policy

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What does ExternalDNS do?
2. How does ExternalDNS authenticate with Route53 on EKS?
3. What problem does a service mesh solve?
4. What is the difference between Istio control plane and data plane?
5. What is mTLS and why is it valuable in microservices?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 4 labs
- [ ] Debugged PI-27
- [ ] Answered interview questions
- [ ] Notes written
