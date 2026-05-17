# Day 69 — CKA Practice — Cluster Ops & Upgrades

> **Phase:** 11 — Certification | **Week:** Week 11 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. kubeadm Cluster Lifecycle
- kubeadm init — control plane bootstrap
- kubeadm join — worker registration
- kubeadm upgrade plan / apply — minor version bumps
- kubeadm reset — clean teardown

### 2. etcd Backup & Restore
- etcdctl snapshot save with cacert/cert/key flags
- Restore: --data-dir=/var/lib/etcd-restored then update manifest
- Verify endpoint health before relying on restore
- Common gotcha: etcd manifest path under /etc/kubernetes/manifests/

### 3. Node Lifecycle
- kubectl drain --ignore-daemonsets --delete-emptydir-data
- kubectl cordon / uncordon
- Node maintenance: drain → patch OS → uncordon
- Force-evict stuck pods (use sparingly)

### 4. kubelet Troubleshooting
- systemctl status kubelet, journalctl -u kubelet
- /var/lib/kubelet/config.yaml — runtime config
- /etc/kubernetes/kubelet.conf — auth config
- Common failures: cert expiry, swap enabled, wrong CRI socket

---

## 🔗 Docs & Resources

- [Cluster Upgrade Docs](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/)
- [etcd Backup Docs](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/)
- [Drain Node](https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Upgrade a kubeadm cluster from N-1 to N (control plane + workers)
- [ ] **Lab 2:** Take an etcd snapshot, intentionally break a resource, restore from snapshot
- [ ] **Lab 3:** Drain a node, simulate OS patching, uncordon — verify pods reschedule
- [ ] **Lab 4:** Recover a failed kubelet (wrong cgroup driver scenario)
- [ ] **Lab 5:** Rotate an expired apiserver certificate using kubeadm certs renew

---

## 🐛 Production Issue to Debug
> After labs

- **PI-CKA-03:** kubeadm upgrade plan succeeds but apply fails on worker — kubelet wrong version.
- **PI-CKA-04:** etcd restore appears successful but cluster sees old state — wrong --data-dir.

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why does kubeadm upgrade need to be run on each node individually?
2. What does `etcdctl snapshot status` tell you about a backup's integrity?
3. Why is --ignore-daemonsets required when draining?
4. How do you renew kubeadm-managed certificates without downtime?
5. What happens if you skip kubeadm upgrade node on a worker?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-CKA-03
- [ ] Debugged PI-CKA-04
- [ ] Answered interview questions
- [ ] Notes written
