# Day 66 — Disaster Recovery + Cluster Operations

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. etcd Backup and Restore (CKA Critical)
- Backup: etcdctl snapshot save /backup/etcd-$(date +%Y%m%d).db
- Automate: CronJob that runs backup and uploads to S3
- Restore procedure: stop API server, restore snapshot, restart
- Verify restore: check pod/deployment counts match

### 2. Velero — Application Backup
- Backs up K8s resources + PVC data (via Restic/Kopia)
- Schedule: VeleroSchedule for regular backups to S3
- Restore: velero restore create from a backup
- Use case: disaster recovery, cluster migration

### 3. Pod Disruption Budget (PDB)
- Prevents too many pods from being unavailable simultaneously
- minAvailable: minimum pods that must be Running
- maxUnavailable: maximum pods that can be disrupted
- Respected by: node drains, rolling updates, eviction API
- Blocks kubectl drain if it would violate PDB

### 4. Cluster Upgrade (kubeadm)
- Order: control plane first, then worker nodes
- kubeadm upgrade plan: check available versions
- kubeadm upgrade apply v1.XX.0
- Drain node → upgrade kubelet/kubectl → uncordon
- EKS: managed node group update (AWS console or eksctl)

---

## 🔗 Docs & Resources

- [etcd backup](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/)
- [Velero](https://velero.io/docs/)
- [PDB](https://kubernetes.io/docs/tasks/run-application/configure-pdb/)
- [kubeadm upgrade](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create etcd backup CronJob → uploads to S3
- [ ] **Lab 2:** Simulate cluster state corruption → restore from snapshot
- [ ] **Lab 3:** Install Velero, create backup of entire namespace
- [ ] **Lab 4:** Delete the namespace, restore from Velero backup
- [ ] **Lab 5:** Create PDB: minAvailable: 2 on a 3-replica deployment
- [ ] **Lab 6:** Drain a node — verify drain is blocked by PDB if it would violate it
- [ ] **Lab 7:** Upgrade kubeadm cluster one minor version

---

## 🐛 Production Issue to Debug
> After labs

- **PI-64:** Cluster upgrade breaks app — deprecated API version removed, update manifests
- **PI-65:** Node drain blocked by PDB — increase maxUnavailable temporarily for maintenance

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the etcd restore procedure?
2. What does Velero back up that etcd backup does not?
3. What is a Pod Disruption Budget?
4. What is the correct order for upgrading a kubeadm cluster?
5. How does PDB interact with kubectl drain?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-64
- [ ] Debugged PI-65
- [ ] Answered interview questions
- [ ] Notes written
