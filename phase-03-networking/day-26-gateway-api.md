# Day 26 — Gateway API — Modern Ingress

> **Phase:** 3 — Networking | **Week:** Week 5 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Problems with Ingress API
- Annotations are implementation-specific — not portable
- No standard for advanced routing (header-based, weight-based)
- No separation of concerns: infra team vs app team

### 2. Gateway API Resources
- GatewayClass: defines the controller (like IngressClass)
- Gateway: specific listener (port, protocol, TLS)
- HTTPRoute: routing rules (like Ingress rules but more expressive)
- TCPRoute, TLSRoute, GRPCRoute: other protocols

### 3. Role Separation
- Infra team: manages GatewayClass + Gateway
- App team: manages HTTPRoute
- Namespace isolation: HTTPRoute can attach to Gateway cross-namespace

### 4. Advanced Routing
- Header-based routing
- Traffic weight splitting (canary without extra tools)
- URL rewriting and redirects
- Request/response header modification

---

## 🔗 Docs & Resources

- [Gateway API docs](https://gateway-api.sigs.k8s.io/)
- [Gateway API vs Ingress](https://gateway-api.sigs.k8s.io/concepts/api-overview/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install Gateway API CRDs
- [ ] **Lab 2:** Install a Gateway API implementation (e.g., Envoy Gateway or NGINX Gateway Fabric)
- [ ] **Lab 3:** Create GatewayClass + Gateway + HTTPRoute
- [ ] **Lab 4:** Implement canary traffic split: 90% v1, 10% v2 via HTTPRoute weights
- [ ] **Lab 5:** Migrate an existing Ingress resource to Gateway API

---

## 🐛 Production Issue to Debug
> After labs

- **PI-25:** HTTPRoute not routing traffic — Gateway not accepting the route, check status conditions

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the main problems Gateway API solves vs Ingress?
2. What is the role of GatewayClass, Gateway, and HTTPRoute?
3. How does Gateway API enable separation of concerns?
4. How do you implement canary deployments using Gateway API?
5. Is Gateway API a replacement for Ingress?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-25
- [ ] Answered interview questions
- [ ] Notes written
