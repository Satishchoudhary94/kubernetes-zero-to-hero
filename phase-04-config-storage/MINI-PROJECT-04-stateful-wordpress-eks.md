# Mini Project 04 — Stateful WordPress on EKS

> **Type:** Mini Project

---

## 🎯 Goal

Deploy a production-grade WordPress site on EKS with persistent MySQL storage, automatic TLS, externally managed secrets, and daily volume snapshots.

---

## 🛠️ Stack

- EKS
- EBS CSI driver
- StatefulSet
- External Secrets Operator
- AWS Secrets Manager
- cert-manager
- NGINX Ingress
- VolumeSnapshots
- CronJob

---

## 📋 Tasks

- [ ] Create EKS cluster with EBS CSI managed add-on
- [ ] Store MySQL root password and WordPress DB password in AWS Secrets Manager
- [ ] Deploy ESO and create ExternalSecrets for both passwords
- [ ] Deploy MySQL as StatefulSet with EBS gp3 PVC
- [ ] Deploy WordPress as Deployment with EFS PVC (for RWX shared uploads)
- [ ] Create ClusterIP Services for MySQL (headless) and WordPress
- [ ] Create Ingress with cert-manager TLS annotation
- [ ] Create VolumeSnapshotClass for EBS
- [ ] Create CronJob that snapshots MySQL PVC daily
- [ ] Verify full site accessible via HTTPS

---

## 🐛 Break-and-Fix (inject after building)

- [ ] PI-32: Delete StorageClass — WordPress fails to provision new PVC
- [ ] PI-29: Expire the ESO sync — MySQL secret becomes stale
- [ ] PI-34: Simulate bad MySQL pod restart — verify data persists from PVC

---

## ✅ Done When

- [ ] WordPress accessible at HTTPS with valid cert
- [ ] MySQL data survives pod restarts
- [ ] Passwords managed via AWS Secrets Manager (not in YAML)
- [ ] Daily snapshot CronJob running
- [ ] All 3 break-fix scenarios debugged
