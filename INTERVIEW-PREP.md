# 🎤 Kubernetes Interview Prep — 150+ Questions by Topic

> Curated questions you'll be asked in Kubernetes platform/SRE/DevOps interviews. Answer them in your own words in `my-notes/`. Don't memorize — internalize.

---

## 📑 Table of Contents

1. [Architecture](#architecture)
2. [Workloads](#workloads)
3. [Networking](#networking)
4. [Storage](#storage)
5. [Security](#security)
6. [Scaling & Scheduling](#scaling--scheduling)
7. [Advanced (Helm, Operators, CRDs)](#advanced)
8. [Observability](#observability)
9. [Troubleshooting](#troubleshooting)
10. [Production & GitOps](#production--gitops)
11. [Scenario / System Design](#scenario--system-design)

---

## Architecture

1. Walk me through what happens when you run `kubectl apply -f deploy.yaml`.
2. Why is etcd's Raft consensus important, and what breaks if you lose quorum?
3. What's the role of the controller manager vs the scheduler?
4. How does the API server authenticate a request? List the chain.
5. Why is the API server stateless? Where does state actually live?
6. What's a control plane vs a data plane in Kubernetes?
7. How does kubelet communicate with the API server, and what's the cert chain?
8. Why does Kubernetes use a level-triggered (not edge-triggered) model?
9. How does the scheduler decide where to place a pod?
10. What's the difference between a controller and an operator?

## Workloads

11. Deployment vs StatefulSet vs DaemonSet — give a real use case for each.
12. Why do StatefulSet pods get stable names but Deployment pods don't?
13. What happens to a PVC when you scale down a StatefulSet?
14. Explain the Deployment rollout process — what are revisions and where are they stored?
15. Why can't you have two Deployments managing the same ReplicaSet?
16. When would you choose a Job over a Deployment?
17. How does CronJob handle missed schedules?
18. What's a sidecar pattern vs an ambassador pattern vs an adapter?
19. Why do init containers run sequentially, not in parallel?
20. What's the difference between restartPolicy: Always, OnFailure, Never?

## Networking

21. Walk me through a packet from pod A to pod B on a different node.
22. What does the CNI plugin actually do at pod creation?
23. ClusterIP, NodePort, LoadBalancer, ExternalName — when and why?
24. How does kube-proxy implement a Service? iptables vs IPVS tradeoffs.
25. What's an Endpoint vs EndpointSlice, and why was EndpointSlice introduced?
26. How does CoreDNS resolve `my-svc.my-ns.svc.cluster.local`?
27. Why might a Service have an empty endpoints list?
28. Ingress vs Gateway API — when would you migrate?
29. NetworkPolicy: default-deny vs default-allow — what's the trap?
30. How does Cilium differ from Calico in implementation?

## Storage

31. What's the difference between a PV and a PVC, conceptually?
32. ReclaimPolicy: Retain vs Delete — when would you choose each?
33. AccessModes: RWO, ROX, RWX, RWOP — give a real use case for each.
34. Why is a StorageClass needed for dynamic provisioning?
35. How does volume expansion work, and why doesn't every CSI driver support it?
36. What's the difference between an emptyDir and a hostPath?
37. CSI Snapshots — what's the workflow?
38. Why are projected volumes useful?
39. How does the Downward API differ from a ConfigMap?
40. What happens to a PV if the PVC is deleted with Retain policy?

## Security

41. RBAC: Role vs ClusterRole vs RoleBinding vs ClusterRoleBinding.
42. How does IRSA work end-to-end (OIDC, trust policy, token projection)?
43. Why is PodSecurityPolicy deprecated, and what replaced it?
44. Pod Security Standards: privileged, baseline, restricted — what changes?
45. What's the difference between AppArmor and seccomp?
46. How does image signing (cosign) actually verify at admission time?
47. Why is `automountServiceAccountToken: false` important?
48. How does an admission webhook differ from a validating policy in Kyverno?
49. What goes in an audit log policy, and what level (None/Metadata/Request/RequestResponse)?
50. How would you detect a compromised pod at runtime?

## Scaling & Scheduling

51. HPA vs VPA — can they coexist? What's the conflict?
52. How does HPA compute desired replicas? Walk me through the math.
53. When would you use KEDA over HPA?
54. Cluster Autoscaler vs Karpenter — what's different?
55. Taints, tolerations, and affinity — what problem does each solve?
56. What's a topology spread constraint? Give a real scenario.
57. ResourceQuota vs LimitRange — when do you need both?
58. Priority and preemption — when does the scheduler evict?
59. What's QoS class, and how does it affect eviction?
60. Why might HPA scale up but pods stay Pending?

## Advanced

61. What's a CRD? When would you write one vs use Helm values?
62. Operator pattern — explain reconciliation loop.
63. Helm vs Kustomize — when each shines.
64. What's Server-Side Apply solving that client-side apply didn't?
65. Why do finalizers block deletion, and how can they cause stuck resources?
66. ValidatingAdmissionWebhook vs MutatingAdmissionWebhook — order of execution?
67. What's a conversion webhook for CRDs?
68. How does Helm rollback work?
69. What's the difference between `helm install` and `helm upgrade --install`?
70. When would you reach for Kustomize overlays instead of Helm conditionals?

## Observability

71. The four golden signals — what are they?
72. Liveness vs readiness vs startup probe — when does each fire?
73. Why might a liveness probe make an outage worse?
74. How does Prometheus discover pods to scrape?
75. ServiceMonitor vs PodMonitor — when to use each?
76. What's a recording rule vs an alerting rule?
77. How does Loki differ from Elasticsearch for logs?
78. What does OpenTelemetry actually standardize?
79. How would you correlate a trace, a log, and a metric for the same request?
80. What's cardinality, and why does it kill Prometheus?

## Troubleshooting

81. Walk me through debugging `CrashLoopBackOff`.
82. Walk me through debugging `ImagePullBackOff`.
83. Walk me through debugging `Pending` for 10 minutes.
84. Walk me through debugging a Service that exists but has no endpoints.
85. Walk me through debugging `dial tcp: lookup my-svc: no such host`.
86. Walk me through debugging a pod that gets OOMKilled at random times.
87. Walk me through debugging a node going `NotReady`.
88. How does `kubectl debug` work, and when do you use ephemeral containers?
89. What does `kubectl get events --sort-by='.lastTimestamp'` tell you that `describe` doesn't?
90. How do you debug an intermittent failure across pods on the same node?

## Production & GitOps

91. ArgoCD vs Flux — what's the architectural difference?
92. Why is "the cluster is the source of truth" wrong in GitOps?
93. Canary vs blue/green vs rolling — give a real scenario for each.
94. How does Argo Rollouts measure canary health?
95. Why is service mesh useful beyond just mTLS?
96. Istio vs Linkerd vs Cilium service mesh — tradeoffs?
97. Velero — what does it back up, what doesn't it?
98. RTO vs RPO — give realistic numbers for an EKS cluster.
99. How does Karpenter consolidation differ from cluster-autoscaler scale-down?
100. What's a soft vs hard multi-tenancy model?

## Scenario / System Design

101. Design a multi-region Kubernetes deployment with active-active failover.
102. You have a stateful workload that needs zero data loss on node failure. How?
103. A pod in tenant A is reading secrets from tenant B. How do you find it and prevent it?
104. Your CI deploys directly with `kubectl apply`. Convince the team to switch to GitOps.
105. A canary deploys to 10%, error rate spikes, but the rollout doesn't auto-rollback. Where's the bug?
106. Design a platform that lets devs self-serve a namespace with quotas and RBAC.
107. You're at 80% node memory cluster-wide every weekday at 9am. What's your action plan?
108. A nightly Job uses 100% of the cluster's IPs and breaks pod scheduling. Fix it.
109. Your team wants to roll out a new CNI without downtime. Walk me through.
110. Design a disaster-recovery runbook for total etcd loss.

---

## 🎯 How to Use This File

- **One topic per week** as you complete the corresponding phase.
- **Write answers in `my-notes/interview-XX-{topic}.md`.**
- **Re-answer the same questions a month later** — the gap exposes weak spots.
- **Record yourself answering 5 questions out loud.** This is the real exam.

> If you can answer 80% of these confidently, you'll pass any Kubernetes interview.
