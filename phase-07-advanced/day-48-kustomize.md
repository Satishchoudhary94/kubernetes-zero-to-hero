# Day 48 — Kustomize

> **Phase:** 7 — Advanced | **Week:** Week 9 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Kustomize vs Helm
- Kustomize: patch existing YAML — no templating language
- Helm: full templating, package management
- Kustomize built into kubectl: `kubectl apply -k`
- When to use: environment-specific overrides without full Helm complexity

### 2. Kustomize Structure
- kustomization.yaml: entry point for kustomize
- resources[]: base YAML files to include
- patches: modify specific fields (strategic merge or JSON6902)
- images[]: override image tags
- namePrefix / nameSuffix: rename all resources

### 3. Base + Overlays Pattern
- base/: common resources shared across environments
- overlays/dev/, overlays/staging/, overlays/prod/: environment-specific
- Overlay only patches the differences

### 4. Generators
- configMapGenerator: generate ConfigMap from files
- secretGenerator: generate Secret from files (hash suffix for rolling updates)
- Hash suffix: auto-updates pods when ConfigMap changes

---

## 🔗 Docs & Resources

- [Kustomize docs](https://kustomize.io/)
- [Kustomize reference](https://kubectl.docs.kubernetes.io/references/kustomize/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a base kustomization for a 3-tier app
- [ ] **Lab 2:** Create dev/staging/prod overlays with different replica counts and images
- [ ] **Lab 3:** Apply: `kubectl apply -k overlays/prod/`
- [ ] **Lab 4:** Use strategic merge patch to add a sidecar to prod only
- [ ] **Lab 5:** Use JSON6902 patch to change a specific field
- [ ] **Lab 6:** Use secretGenerator with hash suffix — verify pods auto-update

---

## 🐛 Production Issue to Debug
> After labs

- **PI-48:** Kustomize overlay not applying — wrong patch path in JSON6902 patch

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between Kustomize and Helm?
2. What is the base + overlays pattern?
3. What is a strategic merge patch vs JSON6902 patch?
4. What does secretGenerator's hash suffix accomplish?
5. How do you apply a Kustomize configuration?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-48
- [ ] Answered interview questions
- [ ] Notes written
