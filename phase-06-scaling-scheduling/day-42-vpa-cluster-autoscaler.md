# Day 42 — VPA + Cluster Autoscaler + Karpenter

> **Phase:** 6 — Scaling + Scheduling | **Week:** Week 8 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. VPA — Vertical Pod Autoscaler
- Right-sizes resource requests/limits automatically
- Modes: Off (recommendations only), Initial (set on create), Auto (live update)
- Components: Recommender, Updater, Admission Plugin
- Limitation: Auto mode restarts pods to apply new resources
- Do NOT use HPA (CPU) + VPA (CPU) together — conflict

### 2. Cluster Autoscaler
- Scales node groups when pods are Pending (unschedulable)
- Scales down when nodes are underutilized
- EKS: integrates with Auto Scaling Groups
- Annotations to prevent scale-down: cluster-autoscaler.kubernetes.io/safe-to-evict
- Expander: how CA chooses which node group to expand

### 3. Karpenter (Modern CA Alternative)
- AWS-native node provisioner for EKS
- NodePool: defines what instances are allowed
- NodeClass: EC2-specific config (AMI, subnets, security groups)
- Faster than CA: provisions nodes in ~30s vs CA's 2–3 min
- Bin-packing: consolidates pods to minimize node count
- Spot interruption handling built-in

### 4. CA vs Karpenter
- CA: works with pre-defined node groups
- Karpenter: creates any instance type on demand
- Karpenter: much more cost-efficient on Spot

---

## 🔗 Docs & Resources

- [VPA](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler)
- [Cluster Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler)
- [Karpenter](https://karpenter.sh/docs/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install VPA, create VPA object with mode: Off, check recommendations
- [ ] **Lab 2:** Set VPA to Initial mode — deploy new pods, verify requests set automatically
- [ ] **Lab 3:** Install Cluster Autoscaler on EKS, set min/max for node group
- [ ] **Lab 4:** Create pods that exceed current capacity — watch CA provision a node
- [ ] **Lab 5:** Install Karpenter on EKS, create NodePool and NodeClass
- [ ] **Lab 6:** Compare provisioning speed: CA vs Karpenter (time from pending to node ready)

---

## 🐛 Production Issue to Debug
> After labs

- **PI-42:** CA not scaling — max node count reached in ASG, needs ASG max increase

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is VPA and what are its 3 modes?
2. Why can't you use HPA (CPU) and VPA (CPU) together?
3. What triggers Cluster Autoscaler to add nodes?
4. What is Karpenter and how is it different from Cluster Autoscaler?
5. How does Karpenter handle Spot interruptions?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-42
- [ ] Answered interview questions
- [ ] Notes written
