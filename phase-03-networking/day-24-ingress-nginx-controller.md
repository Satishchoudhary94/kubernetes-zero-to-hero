# Day 24 — Ingress + NGINX Ingress Controller

> **Phase:** 3 — Networking | **Week:** Week 5 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Ingress Resource vs Ingress Controller
- Ingress: Kubernetes API object that defines routing rules
- Ingress Controller: actual implementation (NGINX, ALB, Traefik)
- Without a controller, Ingress objects do nothing
- Multiple controllers can coexist (IngressClass)

### 2. NGINX Ingress Controller
- Deployed as Deployment + Service (LoadBalancer)
- Reads Ingress objects and dynamically updates nginx.conf
- Annotations control advanced features
- ConfigMap for global config

### 3. Routing Rules
- Host-based: api.example.com → backend service
- Path-based: /api → backend, / → frontend
- Path types: Prefix, Exact, ImplementationSpecific
- Default backend for unmatched requests

### 4. TLS Termination
- TLS secret in same namespace as Ingress
- spec.tls[].secretName references the secret
- SSL passthrough mode for end-to-end TLS

### 5. Key Annotations
- nginx.ingress.kubernetes.io/rewrite-target
- nginx.ingress.kubernetes.io/proxy-body-size
- nginx.ingress.kubernetes.io/rate-limit
- nginx.ingress.kubernetes.io/ssl-redirect

---

## 🔗 Docs & Resources

- [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/)
- [IngressClass](https://kubernetes.io/docs/concepts/services-networking/ingress/#ingress-class)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install NGINX Ingress Controller via Helm
- [ ] **Lab 2:** Create an Ingress with host-based routing to two services
- [ ] **Lab 3:** Create an Ingress with path-based routing
- [ ] **Lab 4:** Configure TLS with a self-signed certificate
- [ ] **Lab 5:** Test rate limiting with an annotation
- [ ] **Lab 6:** Debug a 502 error — identify the backend pod issue

---

## 🐛 Production Issue to Debug
> After labs

- **PI-23:** Ingress returning 502 — backend pods not passing readiness probe

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between an Ingress resource and an Ingress Controller?
2. How does NGINX Ingress Controller work internally?
3. What is an IngressClass?
4. How do you configure TLS for an Ingress?
5. What is the difference between path type Prefix and Exact?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-23
- [ ] Answered interview questions
- [ ] Notes written
