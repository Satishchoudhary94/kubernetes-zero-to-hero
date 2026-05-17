# Day 33 — PV + PVC + StorageClasses

> **Phase:** 4 — Config + Storage | **Week:** Week 6 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Storage Concepts
- PersistentVolume (PV): cluster-scoped storage resource
- PersistentVolumeClaim (PVC): namespace-scoped storage request
- StorageClass: defines how storage is dynamically provisioned
- Binding: PVC binds to PV when requirements match

### 2. Access Modes
- ReadWriteOnce (RWO): one node read-write (EBS)
- ReadOnlyMany (ROX): many nodes read-only
- ReadWriteMany (RWX): many nodes read-write (EFS, NFS)
- ReadWriteOncePod (RWOP): one pod read-write (K8s 1.22+)

### 3. Reclaim Policies
- Delete: PV deleted when PVC deleted (default for dynamic)
- Retain: PV kept after PVC deleted (manual cleanup)
- Recycle: deprecated

### 4. Dynamic Provisioning with StorageClass
- provisioner: specifies the storage driver (ebs.csi.aws.com)
- parameters: storageClass-specific (type, iops, throughput)
- volumeBindingMode: Immediate vs WaitForFirstConsumer
- WaitForFirstConsumer: wait until pod is scheduled (zone-aware)

### 5. EBS StorageClass on EKS
- EBS CSI driver (managed add-on on EKS)
- gp3 StorageClass for general workloads
- io2 for high IOPS databases
- EBS is RWO only — one pod, one node

---

## 🔗 Docs & Resources

- [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
- [StorageClasses](https://kubernetes.io/docs/concepts/storage/storage-classes/)
- [EBS CSI driver](https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create a PV and PVC manually (static provisioning), bind them
- [ ] **Lab 2:** Create a StorageClass with EBS CSI (or hostPath for local lab)
- [ ] **Lab 3:** Create a PVC against StorageClass — verify dynamic provisioning
- [ ] **Lab 4:** Mount PVC in a pod, write data, delete pod, create new pod, verify data persists
- [ ] **Lab 5:** Try to mount an RWO PVC on two pods — observe second pod stuck Pending
- [ ] **Lab 6:** Test WaitForFirstConsumer: verify PVC stays unbound until pod is scheduled

---

## 🐛 Production Issue to Debug
> After labs

- **PI-32:** PVC stuck in Pending — no StorageClass matches volumeName or storageClassName
- **PI-33:** Pod stuck Pending — RWO PVC already mounted on different node

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the difference between a PV and a PVC?
2. What are the 4 access modes and when do you use each?
3. What is the difference between Retain and Delete reclaim policy?
4. What is WaitForFirstConsumer and why is it important on EKS?
5. Why can't you use EBS for a ReadWriteMany workload?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-32
- [ ] Debugged PI-33
- [ ] Answered interview questions
- [ ] Notes written
