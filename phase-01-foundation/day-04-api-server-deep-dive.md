# Day 04 — API Server — Deep Dive

> **Phase:** 1 — Foundation | **Week:** Week 1 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. API Server Request Pipeline
- Step 1: TLS termination
- Step 2: Authentication (certs, bearer tokens, OIDC)
- Step 3: Authorization (RBAC, ABAC, Webhook)
- Step 4: Admission Control (mutating → validating)
- Step 5: Schema validation
- Step 6: Persist to etcd

### 2. API Groups and Versioning
- Core group (v1): pods, services, configmaps, secrets
- Named groups: apps/v1, batch/v1, networking.k8s.io/v1
- Alpha (v1alpha1) → Beta (v1beta1) → GA (v1) lifecycle
- kubectl api-resources and kubectl api-versions
- API deprecation policy

### 3. Watch Mechanism
- Long-polling HTTP watch — how controllers get notified
- resourceVersion and list-watch pattern
- Informers and the local cache (used by controllers)

### 4. Authentication Methods
- X.509 client certificates
- Bearer tokens (ServiceAccount tokens)
- OIDC (AWS SSO, GitHub, Okta)
- kubeconfig structure: clusters, users, contexts

---

## 🔗 Docs & Resources

- [API Server authentication](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)
- [API Groups](https://kubernetes.io/docs/reference/using-api/)
- [Admission controllers](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Decode your kubeconfig certificate: `openssl x509 -in <cert> -text -noout`
- [ ] **Lab 2:** List all API resources: `kubectl api-resources -o wide`
- [ ] **Lab 3:** List all API versions: `kubectl api-versions`
- [ ] **Lab 4:** Use `kubectl --v=8 get pods` to see the raw HTTP requests made
- [ ] **Lab 5:** Enable the dry-run admission chain: `kubectl apply --dry-run=server -f pod.yaml`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-02:** Certificate expired in kubeconfig — locked out of cluster, recovery steps

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the stages a request goes through before hitting etcd?
2. What is the difference between mutating and validating admission controllers?
3. What is an API group and how does versioning work in Kubernetes?
4. How do you check what API versions are available in your cluster?
5. What is the watch mechanism and how do controllers use it?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-02
- [ ] Answered interview questions
- [ ] Notes written
