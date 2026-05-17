# Day 49 — CRDs + Operators

> **Phase:** 7 — Advanced | **Week:** Week 9 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Custom Resource Definitions (CRDs)
- Extend Kubernetes API with custom resource types
- CRD defines: group, version, kind, schema, scope
- After CRD created: kubectl can CRUD the new resource
- Validation: OpenAPI v3 schema in CRD spec
- Subresources: status, scale

### 2. Operator Pattern
- CRD + Controller = Operator
- Encodes operational knowledge as code
- Replaces manual runbooks with automated reconciliation
- Examples: postgres-operator, cert-manager, prometheus-operator

### 3. Building an Operator
- controller-runtime: Go library for building operators
- kubebuilder: scaffolding tool for operators
- Reconciler interface: Reconcile(ctx, req) result
- Client: read/write K8s objects from controller
- Status subresource: report observed state

### 4. Real-World Operators
- cert-manager: manages TLS certificates
- External Secrets Operator: manages external secrets
- ArgoCD: manages GitOps deployments
- Prometheus Operator: manages Prometheus instances

---

## 🔗 Docs & Resources

- [CRDs](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/)
- [kubebuilder](https://book.kubebuilder.io/)
- [controller-runtime](https://pkg.go.dev/sigs.k8s.io/controller-runtime)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a simple CRD: `Website` with spec.url field
- [ ] **Lab 2:** Create a custom resource of type Website
- [ ] **Lab 3:** Write a controller that creates a Deployment + Service for each Website
- [ ] **Lab 4:** Test: create Website resource → controller creates app automatically
- [ ] **Lab 5:** Add status subresource: report URL as ready/not-ready
- [ ] **Lab 6:** Install an existing operator (postgres-operator) and use it

---

## 🐛 Production Issue to Debug
> After labs

- **PI-49:** CRD validation rejecting valid resource — schema too strict, debug OpenAPI spec

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a CRD and a ConfigMap for custom config?
2. What is the Operator pattern?
3. How does a controller know when to reconcile?
4. What is controller-runtime?
5. Give 3 examples of production Kubernetes operators.

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-49
- [ ] Answered interview questions
- [ ] Notes written
