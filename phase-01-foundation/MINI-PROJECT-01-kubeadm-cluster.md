# Mini Project 01 — kubeadm Cluster from Scratch on EC2

> **Type:** Mini Project

---

## 🎯 Goal

Provision a real 3-node Kubernetes cluster on AWS EC2 using kubeadm. Install CNI, validate the cluster, then upgrade it one minor version.

---

## 🛠️ Stack

- kubeadm
- kubelet
- kubectl
- containerd
- Calico CNI
- AWS EC2 (3 instances)
- t3.medium or t3.large

---

## 📋 Tasks

- [ ] Provision 3 EC2 instances: 1 control-plane, 2 workers (Ubuntu 22.04)
- [ ] Install containerd on all nodes, configure as CRI
- [ ] Install kubeadm, kubelet, kubectl on all nodes
- [ ] Disable swap on all nodes
- [ ] Run `kubeadm init` on control-plane node
- [ ] Install Calico CNI
- [ ] Join both worker nodes with `kubeadm join`
- [ ] Verify: all nodes Ready, all system pods Running
- [ ] Deploy a test nginx deployment across worker nodes
- [ ] Drain a worker node, verify pods reschedule
- [ ] Upgrade the cluster one minor version using `kubeadm upgrade`
- [ ] Take an etcd snapshot before the upgrade
- [ ] Document every command used

---

## 🐛 Break-and-Fix (inject after building)

- [ ] Stop the kubelet on a worker — observe NodeNotReady, pods evicted
- [ ] Break the kube-apiserver static pod manifest — observe cluster lockout
- [ ] Restore from etcd snapshot after intentional state corruption

---

## ✅ Done When

- [ ] kubectl get nodes shows all 3 nodes in Ready state
- [ ] kubectl get pods -n kube-system — all control plane pods Running
- [ ] Nginx deployment running with pods spread across worker nodes
- [ ] Cluster upgraded to target version successfully
- [ ] etcd backup exists and restore was tested
