# Mini Project 08 — CKA Killer.sh Mock Exam Simulation

> **Type:** Mini Project

---

## 🎯 Goal

Run a full 2-hour CKA mock exam under real conditions: timed, no external help beyond kubernetes.io, single shell session. Goal: pass at 75%+ to predict real-exam success.

---

## 🛠️ Stack

- killer.sh CKA simulator (or self-built kind/minikube cluster with custom tasks)
- Stopwatch / timer set to 120 minutes hard cap
- Browser bookmarks limited to kubernetes.io/docs only
- Note-taking doc to record skipped tasks and recovery strategy

---

## 📋 Tasks

- [ ] Set up environment 10 minutes before start: aliases, $do export, vim/nano config
- [ ] Print task list, mark dependencies (which tasks require previous task's output)
- [ ] Solve in order of point value: scan all tasks first, tackle high-value first
- [ ] Set per-task budget: if 7-point task takes >12 min, skip and return
- [ ] Track time on each task — write down completion time
- [ ] Last 15 minutes: revisit skipped tasks, never declare done without `kubectl get -A` verify
- [ ] Post-exam: score yourself, identify slowest 3 domains, schedule re-study

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Context switch sabotage: solve a task on cluster A, then verify on cluster B
- [ ] Network policy denies kubectl exec — debug from within a different pod
- [ ] etcd backup corrupted — practice manual recovery without snapshot
- [ ] Killed kubelet on a worker — recover without reinstalling cluster

---

## ✅ Done When

- [ ] Completed all tasks within 120 minutes
- [ ] Scored ≥75% on killer.sh (real exam tends to be easier)
- [ ] Identified weakest 3 domains, logged study plan for each
- [ ] Aliases and $do export are muscle memory, not lookup
- [ ] Saved second killer.sh session for the week before real exam
