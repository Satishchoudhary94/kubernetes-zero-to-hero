# 🎓 Capstone Project — Production-Grade Multi-Tenant Kubernetes Platform

> **Type:** Capstone | **Platform:** AWS EKS | **Duration:** 2–3 weeks | **Prereq:** All 67 days + phase 11

---

## 🎯 Goal

Design, build, and operate a **production-grade multi-tenant Kubernetes platform** that combines everything from the previous 11 phases. The platform serves three internal "tenant" teams running real workloads, with isolation, observability, GitOps delivery, security hardening, and disaster recovery — all running on a single EKS cluster.

This is the project you put on your resume.

---

## 🏗️ Architecture

- **Compute:** EKS 1.30+ with mixed managed node groups + Karpenter for spot
- **Networking:** VPC CNI + Cilium for NetworkPolicies, AWS Load Balancer Controller, ExternalDNS, cert-manager with Let's Encrypt
- **Multi-tenancy:** 3 namespaces (`tenant-a`, `tenant-b`, `tenant-c`) with ResourceQuotas, LimitRanges, NetworkPolicies (default-deny), and tenant-scoped RBAC
- **GitOps:** ArgoCD with app-of-apps; per-tenant `AppProject` to scope what each team can deploy
- **CI:** GitHub Actions → OIDC → AWS → ECR push → ArgoCD auto-sync
- **Observability:** kube-prometheus-stack, Loki, Tempo, Grafana with per-tenant dashboards
- **Progressive delivery:** Argo Rollouts with Prometheus-based analysis on at least one tenant's prod app
- **Security:** PSS `restricted` enforced, Kyverno policies, image signing with cosign, Falco for runtime, EKS audit logs to CloudWatch
- **Backup/DR:** Velero with S3, scheduled snapshots, documented restore runbook
- **Cost:** Karpenter consolidation, KEDA for event-driven scale-to-zero, cost-allocation tags per tenant

---

## 📋 Build Phases

### Phase 1 — Foundation (Week 1, Days 1–3)
- [ ] Terraform module for EKS cluster: VPC, subnets, IAM, OIDC provider
- [ ] Install AWS LB Controller, ExternalDNS, cert-manager via Helm
- [ ] Install Cilium as CNI replacement, verify Hubble UI works
- [ ] Bootstrap ArgoCD, point at config repo, create app-of-apps

### Phase 2 — Multi-Tenancy (Week 1, Days 4–5)
- [ ] Create 3 tenants: namespace, ResourceQuota, LimitRange, default-deny NetworkPolicy
- [ ] RBAC: per-tenant Role + RoleBinding, no cluster-admin escape
- [ ] ArgoCD AppProject per tenant — source repos and target namespaces locked down
- [ ] Apply Pod Security Standards: `baseline` on tenant-a, `restricted` on tenant-b/c

### Phase 3 — Workloads (Week 2, Days 6–8)
- [ ] Deploy 3 real apps (one per tenant): pick from your prior mini-projects
- [ ] Configure HPA on all, VPA in recommend mode, KEDA for event-driven app
- [ ] Set up Ingress per tenant with TLS via cert-manager + Let's Encrypt
- [ ] Add probes (liveness/readiness/startup) tuned for each app's startup time

### Phase 4 — Observability (Week 2, Days 9–10)
- [ ] Install kube-prometheus-stack, Loki, Tempo via Helm
- [ ] Build per-tenant Grafana dashboard: pod count, CPU/mem, error rate, p95 latency
- [ ] ServiceMonitor for each tenant app, alert rules for SLO violations
- [ ] OpenTelemetry sidecar on one app → traces visible in Tempo

### Phase 5 — Security (Week 3, Days 11–12)
- [ ] Install Kyverno, write 5 policies: no-latest-tag, require-resources, no-privileged, require-PDB, signed-images
- [ ] Install cosign, sign one app's images, enforce signature via Kyverno
- [ ] Install Falco with default rules, route alerts to Slack
- [ ] Enable EKS control-plane audit logs → CloudWatch → S3 export

### Phase 6 — Delivery & DR (Week 3, Days 13–14)
- [ ] GitHub Actions CI per tenant: test → build → scan (trivy) → sign → push
- [ ] Convert tenant-c prod deploy to Argo Rollout with canary + Prometheus analysis
- [ ] Install Velero, schedule daily backups to S3
- [ ] Run a DR drill: delete a namespace, restore from Velero, verify uptime metrics

---

## 🐛 Inject & Debug (after full build — production issues)

- [ ] **Tenant escape attempt:** tenant-a service account tries to read tenant-b secrets — verify RBAC denies and audit log captures
- [ ] **Bad image push:** tenant publishes unsigned image — Kyverno blocks, ArgoCD shows degraded
- [ ] **Resource exhaustion:** tenant-b runs a Job that requests 1000 cores — ResourceQuota rejects, debug error path
- [ ] **Certificate expiry simulation:** disable cert-manager renewal, watch alerts fire 7 days before expiry
- [ ] **Canary rollback:** push a tenant-c version that fails analysis — verify auto-rollback within 5 min
- [ ] **Node failure:** terminate a node mid-deploy, verify Karpenter provisions replacement and pods reschedule
- [ ] **Backup corruption:** corrupt one Velero snapshot, verify restore from previous snapshot still works
- [ ] **Runtime threat:** shell into a container, verify Falco fires and Slack alert lands within 30s

---

## ✅ Done When

- [ ] All 3 tenants run real workloads with zero cross-tenant escape paths (verified by red-team exercise)
- [ ] One full end-to-end deploy completes in under 10 minutes: git push → CI → ArgoCD → canary → 100%
- [ ] Bad deploys are detected and rolled back automatically without human intervention
- [ ] Per-tenant dashboards show: SLO compliance, cost allocation, security policy violations
- [ ] DR drill: full namespace restored in under 30 minutes with zero data loss
- [ ] All 5 Kyverno policies enforce in production mode (not audit)
- [ ] Documented runbook: incident response, scale-up, scale-down, restore, rotate credentials
- [ ] You can explain every architectural decision to an interviewer in under 90 seconds

---

## 📝 What to Put on Your Resume

> **Built and operated a production-grade multi-tenant Kubernetes platform on AWS EKS** serving 3 isolated teams. Implemented GitOps delivery with ArgoCD and progressive rollouts via Argo Rollouts (canary + Prometheus analysis). Hardened with Kyverno policies, image signing (cosign), Falco runtime detection, and Pod Security Standards `restricted`. Full observability stack (Prometheus, Loki, Tempo, Grafana), Velero-backed disaster recovery (sub-30-min RTO), and Karpenter-driven cost optimization.

---

## 🎤 Capstone Interview Story

After completing this, you should be able to tell a 5-minute story to any interviewer covering:
1. **The problem** — why multi-tenancy, what could break
2. **Trade-offs** — Cilium vs VPC CNI, ArgoCD vs Flux, Kyverno vs OPA
3. **The hardest bug** — pick one PI from above, walk through diagnosis
4. **What you'd do differently** — scaling pain points, what's still manual
