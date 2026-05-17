# Mini Project 06 — Build a Custom Kubernetes Operator

> **Type:** Mini Project

---

## 🎯 Goal

Build a WebApp operator: a CRD that creates Deployment + Service + Ingress automatically from a single custom resource. Package it with Helm.

---

## 🛠️ Stack

- Go
- kubebuilder
- controller-runtime
- Helm
- MutatingWebhook
- cert-manager

---

## 📋 Tasks

- [ ] Initialize kubebuilder project
- [ ] Define WebApp CRD: spec.image, spec.replicas, spec.host
- [ ] Implement reconciler: create/update Deployment, Service, Ingress
- [ ] Add status subresource: report URL and ready condition
- [ ] Write a MutatingWebhook that injects default resource limits if not set
- [ ] Write unit tests for the reconciler
- [ ] Package the operator as Helm chart
- [ ] Deploy the operator to your cluster
- [ ] Create 3 WebApp resources and verify each gets a full stack
- [ ] Scale a WebApp: update spec.replicas — verify operator updates Deployment

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Delete a Deployment managed by the operator — verify operator recreates it
- [ ] Add an orphaned finalizer to a WebApp — observe stuck deletion, remove manually
- [ ] Break webhook TLS cert — observe pod creation blocked, restore

---

## ✅ Done When

- [ ] kubectl get webapps shows 3 resources
- [ ] Each WebApp has a running Deployment, Service, and Ingress
- [ ] Operator reconciles on any change
- [ ] Helm chart installs operator cleanly in a new cluster
- [ ] All 3 break-fix scenarios resolved
