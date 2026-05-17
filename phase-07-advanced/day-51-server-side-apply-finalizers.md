# Day 51 — Server-Side Apply + Finalizers + API Internals

> **Phase:** 7 — Advanced | **Week:** Week 9 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Server-Side Apply (SSA)
- K8s 1.22+ stable: field ownership tracking on server
- Multiple managers can own different fields of same resource
- Conflict: two managers try to own same field
- Force apply: take ownership even if conflict
- Use case: GitOps tools (ArgoCD uses SSA)

### 2. Finalizers
- Strings in metadata.finalizers[]
- Object with finalizers: won't be deleted until all finalizers removed
- Controller is responsible for cleanup + removing its finalizer
- Common use: clean up cloud resources before deleting K8s object
- Danger: orphaned finalizer = object stuck in Terminating

### 3. Owner References + GC
- ownerReferences: parent-child relationship
- Garbage collector: deletes children when owner is deleted
- Cascade options: Background (default), Foreground, Orphan

### 4. Kubernetes API Internals
- API resource discovery: /api and /apis endpoints
- Storage versioning: internal version vs external version
- Conversion webhooks: convert between API versions
- API priority and fairness: prevent API server overload

---

## 🔗 Docs & Resources

- [Server-side apply](https://kubernetes.io/docs/reference/using-api/server-side-apply/)
- [Finalizers](https://kubernetes.io/docs/concepts/workloads/controllers/garbage-collection/#foreground-deletion)
- [Garbage collection](https://kubernetes.io/docs/concepts/architecture/garbage-collection/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Apply a resource with SSA: `kubectl apply --server-side`
- [ ] **Lab 2:** Observe field managers: `kubectl get pod <name> -o yaml | grep manager`
- [ ] **Lab 3:** Create a resource with a custom finalizer string
- [ ] **Lab 4:** Delete the resource — observe it stuck in Terminating
- [ ] **Lab 5:** Remove the finalizer manually — observe deletion completes
- [ ] **Lab 6:** Inspect owner references on a ReplicaSet (owned by Deployment)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-51:** Namespace stuck in Terminating — orphaned resources with finalizers blocking deletion

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is Server-Side Apply and how does it differ from client-side apply?
2. What are finalizers and why do they exist?
3. What happens when you delete a resource that has a finalizer?
4. What are owner references and how do they enable garbage collection?
5. How do you recover a resource stuck in Terminating due to a finalizer?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-51
- [ ] Answered interview questions
- [ ] Notes written
