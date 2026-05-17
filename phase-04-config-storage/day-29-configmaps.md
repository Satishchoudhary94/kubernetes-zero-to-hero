# Day 29 — ConfigMaps

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 2–3 hours

---

## 📚 Topics to Study

### 1. ConfigMap Fundamentals
- Key-value store for non-sensitive configuration
- Created from: literals, files, env files, directories
- Namespace-scoped resource

### 2. Consuming ConfigMaps
- As environment variables: env[].valueFrom.configMapKeyRef
- All keys as env: envFrom[].configMapRef
- As volume (mounted files): volumes[].configMap
- Key difference: env vars baked at pod start, volumes can update live

### 3. Immutable ConfigMaps
- immutable: true prevents accidental changes
- Performance benefit: kubelet stops watching it
- Use for: versioned configs, release artifacts

### 4. Hot Reload Pattern
- Volume-mounted ConfigMaps update within ~60 seconds
- App must watch the file and reload on change
- Tools: Reloader operator (auto-restarts pods on CM change)

---

## 🔗 Docs & Resources

- [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/)
- [Configuring pods with ConfigMaps](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create ConfigMap from literal values, file, and env file
- [ ] **Lab 2:** Consume ConfigMap as env variables in a pod
- [ ] **Lab 3:** Mount ConfigMap as files — verify hot reload (edit CM, watch file update)
- [ ] **Lab 4:** Create an immutable ConfigMap — try to edit it (observe error)
- [ ] **Lab 5:** Install Reloader and verify pod restarts on ConfigMap change

---

## 🐛 Production Issue to Debug
> After labs

- **PI-28:** App not picking up config change — env var from ConfigMap doesn't hot-reload

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the ways to consume a ConfigMap in a pod?
2. What is the difference between envFrom and env[].valueFrom?
3. Why don't environment variable ConfigMaps hot-reload?
4. When should you use an immutable ConfigMap?
5. What is the Reloader pattern?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-28
- [ ] Answered interview questions
- [ ] Notes written
