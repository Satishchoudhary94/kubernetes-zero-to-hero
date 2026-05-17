# Day 47 — Helm — Complete Guide

> **Phase:** 7 — Advanced | **Week:** Week 9 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Helm Concepts
- Chart: package of K8s resources (like apt/npm package)
- Release: installed instance of a chart
- Repository: collection of charts
- Values: customization without modifying templates

### 2. Chart Structure
- Chart.yaml: metadata (name, version, appVersion, dependencies)
- values.yaml: default values
- templates/: Go templating with K8s YAML
- charts/: sub-charts (dependencies)
- _helpers.tpl: reusable template snippets

### 3. Helm Templating
- {{ .Values.xxx }}: access values
- {{ .Release.Name }}: release context
- range: iterate over lists
- if/else: conditional resources
- include / template: reuse helpers
- toYaml + indent: embed nested YAML

### 4. Helm Operations
- helm install / upgrade / rollback / uninstall
- helm diff (plugin): preview changes before upgrade
- helm test: run test pods
- Helm hooks: pre-install, post-upgrade, pre-delete
- OCI registry: push/pull charts from ECR

---

## 🔗 Docs & Resources

- [Helm docs](https://helm.sh/docs/)
- [Helm chart best practices](https://helm.sh/docs/chart_best_practices/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install a public chart: `helm install nginx ingress-nginx/ingress-nginx`
- [ ] **Lab 2:** Build a Helm chart from scratch for a 3-tier app
- [ ] **Lab 3:** Use values override: `helm install myapp ./chart -f prod-values.yaml`
- [ ] **Lab 4:** Use helm diff to preview changes before upgrade
- [ ] **Lab 5:** Add a pre-install Job hook (database migration)
- [ ] **Lab 6:** Publish chart to ECR OCI registry
- [ ] **Lab 7:** Rollback a failed helm upgrade

---

## 🐛 Production Issue to Debug
> After labs

- **PI-47:** Helm release stuck in failed state — how to fix and force upgrade

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a Helm chart and a Helm release?
2. How do Helm hooks work?
3. What is the difference between `helm upgrade` and `helm upgrade --install`?
4. How do you share common templates across charts?
5. How do you rollback a Helm upgrade?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-47
- [ ] Answered interview questions
- [ ] Notes written
