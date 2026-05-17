# Day 68 — CKA Exam — Overview & Strategy

> **Phase:** 11 — Certification | **Week:** Week 11 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. Exam Format (2026)
- 120-minute performance-based exam on a real cluster
- 15–20 tasks across multiple clusters (context switching critical)
- Pass mark: 66%
- Open book — kubernetes.io/docs and kubernetes.io/blog only
- Linux terminal in browser, copy/paste enabled (Ctrl+Shift+C/V)

### 2. Domain Weighting
- Cluster Architecture, Installation & Configuration — 25%
- Workloads & Scheduling — 15%
- Services & Networking — 20%
- Storage — 10%
- Troubleshooting — 30%

### 3. Strategy
- Speed > depth — skip if stuck >5 min, return at end
- Set up aliases on day-of: `alias k=kubectl`, `export do='--dry-run=client -o yaml'`
- kubectl explain over docs search — faster
- Always verify: kubectl get -A before declaring done
- Use `--context` flag explicitly, never assume

### 4. Killer.sh Simulator
- Included free with exam voucher (2 sessions, 36h each)
- Harder than real exam — if you pass killer.sh, you pass CKA
- Use 1 week before exam, save second session for final review

---

## 🔗 Docs & Resources

- [CNCF CKA Curriculum](https://github.com/cncf/curriculum)
- [Linux Foundation CKA](https://www.cncf.io/training/certification/cka/)
- [CKA Tips (Walid Shaari)](https://github.com/walidshaari/Kubernetes-Certified-Administrator)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/quick-reference/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Register for killer.sh free practice (after purchasing voucher)
- [ ] **Lab 2:** Configure exam-environment aliases in your shell rc file
- [ ] **Lab 3:** Practice context switching: kubectl config use-context
- [ ] **Lab 4:** Time yourself: solve 5 random tasks in 30 minutes
- [ ] **Lab 5:** Bookmark 10 kubernetes.io pages you'll need fast access to

---

## 🐛 Production Issue to Debug
> After labs

- **PI-CKA-01:** Wrong context — you applied a fix to the dev cluster instead of prod. Recover.
- **PI-CKA-02:** Out of time on the simulator — practice triage and partial credit strategy.

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What domains carry the most weight on CKA?
2. Why is context switching the #1 source of failed CKA tasks?
3. How does killer.sh differ from the real CKA exam?
4. What is the imperative-to-declarative workflow for fast YAML generation?
5. When is `kubectl edit` faster than `kubectl apply -f`?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-CKA-01
- [ ] Debugged PI-CKA-02
- [ ] Answered interview questions
- [ ] Notes written
