# Day 67 — Cost Optimization + Multi-Cluster

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Kubernetes Cost Optimization
- Kubecost: visibility into cost per namespace, deployment, team
- Goldilocks: VPA-based resource right-sizing recommendations
- Spot instances: 60-90% cheaper, handle interruptions with PDB+HPA
- Bin packing: Karpenter consolidation mode
- Remove idle resources: Kubernetes Resource Report, kube-resource-report

### 2. Right-Sizing Resources
- Goldilocks: installs VPA in recommendation mode per namespace
- Dashboard: shows current vs recommended CPU/memory
- Apply recommendations: update deployment resource requests
- Impact: over-provisioning wastes money, under-provisioning = OOMKill

### 3. Multi-Cluster Patterns
- Why multi-cluster: HA, compliance, team isolation, geo distribution
- Cluster API: GitOps for cluster provisioning
- ArgoCD multi-cluster: one control plane, many destinations
- Service mesh federation: Istio multi-cluster, Cilium cluster mesh
- Global load balancing: Route53 weighted routing across clusters

### 4. EKS Cost Tips
- Fargate for bursty workloads (pay per pod, not per node)
- Savings Plans for steady-state workloads
- Node group rightsizing: match instance type to workload profile
- NAT Gateway costs: use VPC endpoints for AWS services

---

## 🔗 Docs & Resources

- [Kubecost](https://www.kubecost.com/)
- [Goldilocks](https://github.com/FairwindsOps/goldilocks)
- [Cluster API](https://cluster-api.sigs.k8s.io/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install Kubecost, explore cost breakdown by namespace
- [ ] **Lab 2:** Install Goldilocks, view resource recommendations for your deployments
- [ ] **Lab 3:** Right-size 3 deployments based on Goldilocks recommendations
- [ ] **Lab 4:** Set up ArgoCD multi-cluster: deploy same app to 2 clusters
- [ ] **Lab 5:** Calculate monthly savings from Spot instances vs On-Demand

---

## 🐛 Production Issue to Debug
> After labs

- **PI-66:** Unexpected AWS bill spike — Kubecost identifies a runaway batch job consuming 40% of cluster

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. How do you identify which namespace is costing the most?
2. What is Goldilocks and how does it help with cost?
3. What are the trade-offs of Spot instances for Kubernetes?
4. What is Cluster API?
5. How does Karpenter consolidation reduce costs?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-66
- [ ] Answered interview questions
- [ ] Notes written
