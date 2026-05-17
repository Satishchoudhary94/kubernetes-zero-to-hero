# 🚢 Kubernetes Zero to Hero — Production-Ready Learning Path

> **88-file, 11-phase roadmap from beginner to production-grade Kubernetes engineer.**
> Each day: topics to study, official docs, hands-on labs, a production issue to debug, and interview questions. No content dumps — you study from official sources, then prove it in labs.

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE) ![Phases](https://img.shields.io/badge/phases-11-success) ![Days](https://img.shields.io/badge/days-72-blue) ![Projects](https://img.shields.io/badge/projects-12-orange)

---

## 🎯 Who This Is For

- **You know Docker** but Kubernetes still feels like magic.
- **You can `kubectl apply -f`** but can't debug why a pod is `CrashLoopBackOff` in under 5 minutes.
- **You want to pass CKA/CKAD/CKS** and back the cert with real production muscle.
- **You want a resume-worthy capstone** — not another todo-list demo.

If you nodded at any of those, this is for you.

---

## 🗺️ The Path

| Phase | Title | Days | Outcome |
|------:|-------|:----:|---------|
| **0** | Pre-Flight (Containers, Runtimes) | 1–2 | Why Kubernetes exists |
| **1** | Foundation (Architecture → Pods) | 3–13 | Build a cluster from scratch with kubeadm |
| **2** | Workloads | 14–18 | Every controller and when to use it |
| **3** | Networking | 19–28 | Pod-to-pod, services, ingress, gateway API |
| **4** | Config & Storage | 29–34 | ConfigMaps, Secrets, PVs, CSI |
| **5** | Security | 35–40 | RBAC, IRSA, PSS, image security, audit |
| **6** | Scaling & Scheduling | 41–46 | HPA, VPA, KEDA, affinity, topology spread |
| **7** | Advanced | 47–51 | Helm, Kustomize, CRDs, operators, admission |
| **8** | Observability | 52–56 | Prometheus, Loki, Tempo, OpenTelemetry |
| **9** | Troubleshooting | 57–61 | Debugging methodology that actually works |
| **10** | Production | 62–67 | CI/CD, GitOps, service mesh, DR, cost |
| **11** | Certification | 68–72 | CKA, CKAD, CKS prep + killer.sh mock |
| **🎓** | **Capstone** | — | Multi-tenant production platform on EKS |

**Total:** 72 days of structured learning + 7 mini-projects + 4 production projects + 1 capstone.

---

## 📂 Repo Layout

```
phase-00-preflight/         # Container fundamentals
phase-01-foundation/        # K8s architecture, kubeadm cluster
phase-02-workloads/         # Deployment, StatefulSet, DaemonSet, Jobs
phase-03-networking/        # Services, ingress, CNI, gateway-api
phase-04-config-storage/    # ConfigMaps, secrets, CSI, snapshots
phase-05-security/          # RBAC, PSS, audit, image security
phase-06-scaling-scheduling/# HPA, VPA, KEDA, taints, affinity
phase-07-advanced/          # Helm, operators, admission, SSA
phase-08-observability/     # Prometheus, Loki, Tempo, OTEL
phase-09-troubleshooting/   # Debugging real failures
phase-10-production/        # GitOps, mesh, DR, cost optimization
phase-11-certification/     # CKA/CKAD/CKS exam prep
CAPSTONE-PROJECT.md         # The big one
PROGRESS.md                 # Track your journey
INTERVIEW-PREP.md           # 150+ questions by topic
```

Each `day-XX-*.md` file has the same shape:
- 📚 **Topics to Study** — bullet list of concepts
- 🔗 **Docs & Resources** — official Kubernetes docs links only
- 🧪 **Hands-on Labs** — what to build to internalize the topic
- 🐛 **Production Issue to Debug** — a real failure scenario tagged `PI-XX`
- ❓ **Interview Questions** — answer in `my-notes/` after the day
- 📝 **My Notes** — empty section for your own writing
- ✅ **Completion Checklist** — every box must be checked before moving on

---

## 🚀 How to Use This Repo

1. **Clone and create your branch:**
   ```bash
   git clone https://github.com/Satishchoudhary94/kubernetes-zero-to-hero.git
   cd kubernetes-zero-to-hero
   git checkout -b my-progress
   mkdir my-notes
   ```
2. **One day = one session.** Don't skip the labs.
3. **Write your notes in `my-notes/day-XX-yourname.md`** — explaining a concept in your own words is the test.
4. **Mark completion in `PROGRESS.md`.**
5. **Cap every phase with the phase's mini/production project.** No exceptions.
6. **The capstone is non-negotiable.** It's what turns a certificate-holder into someone who's actually built a platform.

---

## 🛠️ Prerequisites

- Comfortable in a Linux shell
- Docker installed locally
- AWS account (free tier is fine for most labs; EKS will cost ~$2/day during the labs that need it)
- 8GB+ RAM for local kubeadm/kind work
- `kubectl`, `helm`, `kind` or `minikube`, `gh` CLI installed

---

## 📚 Companion Resources

- **Books:** *Kubernetes Up & Running* (Hightower), *Programming Kubernetes* (Hausenblas & Schwartz)
- **Docs:** [kubernetes.io/docs](https://kubernetes.io/docs/) — the only doc site you need
- **Practice clusters:** [killercoda.com](https://killercoda.com/), [play-with-k8s.com](https://labs.play-with-k8s.com/)
- **Cert simulator:** [killer.sh](https://killer.sh/) (free with CKA/CKAD/CKS voucher)

---

## 🤝 Contributing

PRs welcome. If you found a production issue not covered here, open an issue with the `PI-` tag and a short repro.

---

## 📜 License

MIT
