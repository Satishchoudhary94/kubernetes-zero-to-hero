# Day 70 — CKA Practice — Workloads, Networking & Storage

> **Phase:** 11 — Certification | **Week:** Week 11 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Fast YAML Generation
- kubectl run nginx --image=nginx $do > pod.yaml
- kubectl create deployment web --image=nginx $do > deploy.yaml
- kubectl expose deploy web --port=80 $do > svc.yaml
- kubectl create job hello --image=busybox $do -- echo hi
- Memorize $do='--dry-run=client -o yaml' alias

### 2. Service Debugging Flow
- kubectl get endpoints — empty endpoints means selector mismatch
- kubectl describe svc — verify selector and ports
- kubectl exec -it test-pod -- nslookup svc-name.ns.svc.cluster.local
- kubectl get networkpolicy -A — is something blocking?

### 3. NetworkPolicy Patterns
- Default-deny ingress + explicit allow
- Egress restriction to specific CIDR or namespace
- Combining podSelector + namespaceSelector
- Testing: install netshoot pod, attempt connections

### 4. Storage Tasks
- Static PV → PVC binding (verify storageClassName matches)
- Dynamic provisioning via StorageClass
- Volume expansion: allowVolumeExpansion + edit PVC
- ReclaimPolicy: Retain vs Delete consequences

---

## 🔗 Docs & Resources

- [kubectl Conventions](https://kubernetes.io/docs/reference/kubectl/conventions/)
- [NetworkPolicy Recipes](https://github.com/ahmetb/kubernetes-network-policy-recipes)
- [Storage Classes](https://kubernetes.io/docs/concepts/storage/storage-classes/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Generate Deployment + Service + Ingress YAML using only imperative commands
- [ ] **Lab 2:** Build a default-deny NetworkPolicy, then allow only one frontend → backend path
- [ ] **Lab 3:** Bind a static PV to a PVC, mount in a Pod, write a file, recreate Pod — verify persistence
- [ ] **Lab 4:** Resize a PVC from 1Gi → 5Gi on a CSI driver that supports expansion
- [ ] **Lab 5:** Debug an empty-endpoints Service (selector typo) under 3 minutes

---

## 🐛 Production Issue to Debug
> After labs

- **PI-CKA-05:** Service shows endpoints but pods can't reach it — kube-proxy mode mismatch.
- **PI-CKA-06:** PVC stays Pending — wrong storageClassName, no matching PV.

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What does `--dry-run=client -o yaml` actually skip?
2. Why does an empty endpoints list almost always mean a selector bug?
3. How does a NetworkPolicy interact with kube-proxy?
4. When does ReclaimPolicy: Delete actually delete the underlying disk?
5. What's the difference between accessModes ReadWriteOnce and ReadWriteOncePod?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-CKA-05
- [ ] Debugged PI-CKA-06
- [ ] Answered interview questions
- [ ] Notes written
