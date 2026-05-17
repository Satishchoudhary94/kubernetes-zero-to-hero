# Day 35 — RBAC — Complete Guide

> **Phase:** 5 — Security | **Week:** Week 7 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. RBAC Objects
- Role: namespace-scoped set of permissions
- ClusterRole: cluster-wide permissions
- RoleBinding: binds Role/ClusterRole to subjects in a namespace
- ClusterRoleBinding: binds ClusterRole to subjects cluster-wide
- Subjects: User, Group, ServiceAccount

### 2. Permissions Model
- API groups + resources + verbs
- Verbs: get, list, watch, create, update, patch, delete
- Resource names (specific object restriction)
- Wildcard: * means all

### 3. Aggregated ClusterRoles
- Aggregate smaller ClusterRoles into larger ones
- Label-based aggregation: aggregationRule + matchLabels
- Built-in: admin, edit, view — all use aggregation

### 4. Debugging RBAC (Critical for CKA)
- kubectl auth can-i <verb> <resource> --as=<user>
- kubectl auth can-i --list --as=<user> -n <namespace>
- Check who bound the role: kubectl get rolebindings -A
- Common mistake: RoleBinding to ClusterRole only works in that namespace

---

## 🔗 Docs & Resources

- [RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
- [kubectl auth can-i](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_auth/kubectl_auth_can-i/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a Role that allows get/list/watch on pods in namespace dev
- [ ] **Lab 2:** Create a RoleBinding binding it to user 'developer'
- [ ] **Lab 3:** Verify with: `kubectl auth can-i get pods --as=developer -n dev`
- [ ] **Lab 4:** Create a ClusterRole for read-only cluster access
- [ ] **Lab 5:** Try: give namespace-level admin access vs cluster-level admin access
- [ ] **Lab 6:** Debug a Forbidden error: trace from error → RoleBinding → Role → missing verb

---

## 🐛 Production Issue to Debug
> After labs

- **PI-35:** CI pipeline getting 403 Forbidden — ServiceAccount missing verb on resource, debug trace

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between Role and ClusterRole?
2. What is the difference between RoleBinding and ClusterRoleBinding?
3. How do you check what permissions a user/SA has?
4. Can a RoleBinding reference a ClusterRole? What is the effect?
5. What verbs are available in Kubernetes RBAC?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-35
- [ ] Answered interview questions
- [ ] Notes written
