# Day 06 — Scheduler + Controller Manager

> **Phase:** 1 — Foundation | **Week:** Week 1 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. kube-scheduler Internals
- Watches for pods with no nodeName set (unscheduled pods)
- Stage 1 — Filtering (Predicates): remove infeasible nodes
- Stage 2 — Scoring (Priorities): rank feasible nodes
- Stage 3 — Binding: write nodeName to pod spec in etcd
- Scheduling plugins: NodeResourcesFit, NodeAffinity, PodTopologySpread
- Multiple schedulers: custom scheduler deployment

### 2. kube-controller-manager
- Runs many controllers as goroutines in a single process
- Key controllers: Deployment, ReplicaSet, Node, Job, Endpoint
- Control loop: watch desired → observe actual → reconcile
- Leader election: only one controller-manager is active

### 3. Controller Reconciliation Pattern
- Informers: local cache + event handlers
- Work queues: rate-limited, retries
- Finalizers: pre-delete hooks
- Owner references: garbage collection

### 4. Lease Objects + Leader Election
- Lease API object: used for leader election
- Why controllers use leader election
- How to check which controller-manager holds the lease

---

## 🔗 Docs & Resources

- [Scheduler docs](https://kubernetes.io/docs/concepts/scheduling-eviction/kube-scheduler/)
- [Writing a custom scheduler](https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/)
- [Controller patterns](https://kubernetes.io/docs/concepts/architecture/controller/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Manually schedule a pod by setting `spec.nodeName` directly (bypass scheduler)
- [ ] **Lab 2:** Watch the scheduler in action: create a deployment and watch events
- [ ] **Lab 3:** Mark a node as unschedulable with `kubectl cordon` and observe scheduler behavior
- [ ] **Lab 4:** Inspect the scheduler's current configuration: `kubectl get configmap -n kube-system`
- [ ] **Lab 5:** Check the leader election lease: `kubectl get lease -n kube-system`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-04:** Controller manager down — ReplicaSets not reconciling, pods not replaced on deletion

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the three stages of Kubernetes scheduling?
2. What is a control loop and how does it implement self-healing?
3. What happens if the kube-scheduler crashes?
4. How does leader election work for the controller manager?
5. What is the difference between a predicate and a priority in scheduling?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-04
- [ ] Answered interview questions
- [ ] Notes written
