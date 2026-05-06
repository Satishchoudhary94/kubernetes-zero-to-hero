# Mini Project 02 — Multi-Tenant Platform Foundation

> **Type:** Mini Project

---

## 🎯 Goal

Build a multi-tenant Kubernetes platform with 3 isolated team namespaces (dev, staging, prod), complete with resource controls, label standards, and debugging capabilities.

---

## 🛠️ Stack

- kubectl
- kind or kubeadm cluster
- ResourceQuota
- LimitRange
- RBAC (preview)
- Labels + Annotations

---

## 📋 Tasks

- [ ] Create namespaces: dev, staging, production
- [ ] Apply different ResourceQuotas per namespace (dev=small, staging=medium, prod=large)
- [ ] Apply LimitRange defaults to all namespaces
- [ ] Label all namespaces with team= and env= labels
- [ ] Deploy a sample app in each namespace
- [ ] Verify resource isolation: can one namespace exceed its quota?
- [ ] Use ephemeral container to debug a running app pod
- [ ] Create a static pod on a worker node
- [ ] Document the quota limits and enforcement

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Remove LimitRange from dev namespace — see pods with no limits created
- [ ] Set quota.pods=2 in dev — try to create 3 pods
- [ ] Create a pod that triggers OOMKill — diagnose from events

---

## ✅ Done When

- [ ] All 3 namespaces exist with correct labels
- [ ] ResourceQuota prevents over-provisioning
- [ ] LimitRange applies defaults automatically
- [ ] Successfully debugged app using ephemeral container
- [ ] Static pod created and verified on worker node
