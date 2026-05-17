# Mini Project 05 — Auto-Scaling SaaS Backend on EKS

> **Type:** Mini Project

---

## 🎯 Goal

Build an auto-scaling backend on EKS that scales pods on CPU (HPA), scales nodes with Karpenter, handles Spot interruptions, and distributes pods across 3 AZs.

---

## 🛠️ Stack

- EKS
- Karpenter
- HPA
- KEDA
- Spot instances
- Topology Spread
- PriorityClass
- k6 (load testing)

---

## 📋 Tasks

- [ ] Create EKS cluster with 3 AZs
- [ ] Install Karpenter with Spot + On-Demand NodePool
- [ ] Deploy backend API Deployment (start with 2 replicas)
- [ ] Configure HPA: CPU target 60%, min 2, max 20
- [ ] Configure KEDA ScaledObject: SQS queue (threshold: 5 messages/pod)
- [ ] Apply Topology Spread: maxSkew 1 across zones
- [ ] Apply pod anti-affinity: no two replicas on same node
- [ ] Create high and low PriorityClass, assign to different workloads
- [ ] Load test with k6: ramp from 0 to 10,000 RPS
- [ ] Watch full scale chain: HPA scales pods → Karpenter adds nodes
- [ ] Verify pods spread across AZs during scale-up
- [ ] Simulate Spot interruption: terminate a Spot node, observe pod migration

---

## 🐛 Break-and-Fix (inject after building)

- [ ] PI-41: Remove metrics-server — HPA stops working, pods not scaling
- [ ] PI-42: Set Karpenter NodePool maxCount too low — nodes stop provisioning
- [ ] PI-44: Remove topology spread — all pods land on one zone

---

## ✅ Done When

- [ ] Under load: HPA scaled pods from 2 to 15+
- [ ] Karpenter provisioned new nodes under 60 seconds
- [ ] Pods distributed across all 3 AZs (verify with kubectl get pods -o wide)
- [ ] Spot interruption handled gracefully (no downtime)
- [ ] All 3 break-fix scenarios debugged
