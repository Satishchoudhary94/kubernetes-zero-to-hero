# Day 63 — GitOps with ArgoCD

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. GitOps Principles
- Git is the single source of truth for cluster state
- Desired state in git, ArgoCD reconciles actual state
- No direct kubectl apply to production — all changes via PR
- Audit trail: every change tracked in git history

### 2. ArgoCD Architecture
- Application: defines source (git) + destination (cluster + namespace)
- AppProject: RBAC + access control for Applications
- ApplicationSet: generate multiple Applications from one template
- Repository server, application controller, API server, Redis

### 3. Sync Policies
- Manual sync: review before applying
- Automatic sync: ArgoCD applies on git push
- Self-heal: fix drift (manual kubectl changes get reverted)
- Prune: remove resources not in git
- syncOptions: CreateNamespace, ServerSideApply

### 4. App-of-Apps Pattern
- One root Application points to a folder of Application YAMLs
- Each Application manages one service or namespace
- Declarative: entire cluster defined in git

### 5. Multi-Cluster ArgoCD
- Register multiple clusters in ArgoCD
- Deploy same app to dev/staging/prod from one ArgoCD
- ApplicationSet with cluster generator: auto-create per cluster

---

## 🔗 Docs & Resources

- [ArgoCD docs](https://argo-cd.readthedocs.io/en/stable/)
- [ApplicationSet](https://argo-cd.readthedocs.io/en/stable/operator-manual/applicationset/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install ArgoCD via Helm
- [ ] **Lab 2:** Create an Application pointing to a Helm chart in GitHub
- [ ] **Lab 3:** Enable auto-sync + self-heal
- [ ] **Lab 4:** Make a direct kubectl change — watch ArgoCD revert it
- [ ] **Lab 5:** Create an AppProject with restricted source repo and destination namespace
- [ ] **Lab 6:** Implement app-of-apps: root app manages 3 child Applications
- [ ] **Lab 7:** Register a second cluster and deploy to it via ArgoCD

---

## 🐛 Production Issue to Debug
> After labs

- **PI-61:** ArgoCD sync stuck — resource hook failing, debug hook job logs

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the 4 GitOps principles?
2. What is the difference between an ArgoCD Application and ApplicationSet?
3. What does auto-sync with self-heal do?
4. What is the app-of-apps pattern?
5. How does ArgoCD handle multi-cluster deployments?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-61
- [ ] Answered interview questions
- [ ] Notes written
