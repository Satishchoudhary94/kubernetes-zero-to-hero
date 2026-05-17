# Production Project 04 — GitOps CI/CD Platform on EKS

> **Type:** Production Project | **Platform:** AWS EKS

---

## 🎯 Goal

Build a complete GitOps platform: GitHub Actions for CI, ArgoCD for CD, Argo Rollouts for progressive delivery, across dev/staging/prod environments.

---

## 🏗️ Architecture

- EKS cluster with 3 namespaces: dev, staging, production
- ArgoCD with app-of-apps managing all environments
- GitHub Actions: test → build → scan → push → trigger ArgoCD sync
- Argo Rollouts: canary with Prometheus analysis gates in production
- Helm charts for all applications
- OIDC GitHub → AWS (no stored keys)
- Slack notifications: deploy start/success/failure/rollback

---

## 📋 Build Phases

### Phase 1: Repository Setup
- [ ] Create app repo (source code) + config repo (Helm values/ArgoCD apps)
- [ ] Set up GitHub Actions workflow for CI
- [ ] Configure OIDC federation: GitHub → AWS

### Phase 2: ArgoCD Setup
- [ ] Install ArgoCD via Helm
- [ ] Create AppProject per environment
- [ ] Create root app-of-apps Application
- [ ] Configure auto-sync for dev, manual for prod

### Phase 3: Progressive Delivery
- [ ] Convert production Deployment to Argo Rollout
- [ ] Create AnalysisTemplate: error rate < 1% via Prometheus
- [ ] Configure canary steps: 10% → 25% → 50% → 100%
- [ ] Test: deploy bad version → watch auto-rollback at 10% step

### Phase 4: Notifications
- [ ] Install ArgoCD notifications
- [ ] Configure Slack: notify on sync-failed, degraded, healthy after rollback

---

## 🐛 Inject & Debug (after full build)

- [ ] PI-61: ArgoCD sync hook fails — app stuck OutOfSync, debug hook job
- [ ] PI-62: Canary AnalysisTemplate no data — Prometheus metric not found, fix query
- [ ] PI-60: CI pushes unsigned image — Kyverno blocks deployment, fix pipeline
- [ ] PI-47: Helm release in failed state after bad upgrade — force-upgrade to fix

---

## ✅ Done When

- [ ] Commit to app repo → CI builds and pushes image within 3 minutes
- [ ] ArgoCD automatically deploys to dev within 1 minute of image push
- [ ] Staging requires manual sync approval
- [ ] Production uses canary: bad deploy detected and rolled back automatically
- [ ] Slack receives notification for all deployment events
- [ ] All 4 injected issues debugged and resolved
