# Day 34 — CSI + Volume Snapshots + Expansion

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. CSI Architecture
- Container Storage Interface: standardized storage plugin API
- CSI driver components: external-provisioner, external-attacher, node-driver-registrar
- Driver runs as DaemonSet (node plugin) + Deployment (controller plugin)
- replaces in-tree volume plugins

### 2. EBS CSI Driver on EKS
- EKS managed add-on (recommended) or self-managed
- Requires IRSA: ec2:CreateVolume, ec2:AttachVolume permissions
- Topology-aware: volumes created in same AZ as pod

### 3. Volume Snapshots
- VolumeSnapshotClass: like StorageClass for snapshots
- VolumeSnapshot: request to create a snapshot
- VolumeSnapshotContent: actual snapshot resource
- Restore: create PVC from VolumeSnapshot

### 4. Volume Expansion
- StorageClass must have allowVolumeExpansion: true
- Edit PVC spec.resources.requests.storage to larger value
- Online expansion: resize while pod is running (ext4, xfs)
- Offline expansion: some drivers need pod stopped

---

## 🔗 Docs & Resources

- [CSI drivers](https://kubernetes-csi.github.io/docs/)
- [Volume snapshots](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)
- [Volume expansion](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install EBS CSI driver as EKS managed add-on
- [ ] **Lab 2:** Create a VolumeSnapshotClass for EBS
- [ ] **Lab 3:** Take a snapshot of a running PostgreSQL PVC
- [ ] **Lab 4:** Restore the snapshot to a new PVC and verify data
- [ ] **Lab 5:** Expand a PVC from 10Gi to 20Gi online
- [ ] **Lab 6:** Create a CronJob that takes daily EBS snapshots

---

## 🐛 Production Issue to Debug
> After labs

- **PI-34:** EBS volume stuck in terminating — EC2 instance terminated abruptly, force detach

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is CSI and why was it created?
2. How does topology-aware provisioning work with EBS?
3. What are VolumeSnapshots and how do you restore from one?
4. How do you expand a PVC?
5. What permissions does the EBS CSI driver need via IRSA?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-34
- [ ] Answered interview questions
- [ ] Notes written
