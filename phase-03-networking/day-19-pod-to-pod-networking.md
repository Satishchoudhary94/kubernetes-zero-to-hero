# Day 19 — Pod-to-Pod Networking Deep Dive

> **Phase:** 3 — Networking | **Week:** Week 4 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Kubernetes Network Model
- Every pod gets a unique cluster-wide IP
- No NAT between pods — flat network
- Pods on same node communicate via bridge (cbr0 / cni0)
- Pods on different nodes: overlay or BGP routing

### 2. Same-Node Communication
- veth pair: one end in pod netns, other in host netns
- Linux bridge: connects all veth pairs on a node
- Packet path: pod-A veth → bridge → pod-B veth

### 3. Cross-Node Communication
- VXLAN overlay: encapsulate L2 frames in UDP (Flannel/Calico default)
- BGP routing: advertise pod CIDRs as routes (Calico BGP mode)
- AWS VPC CNI: pods get VPC IPs directly (no overlay)
- Packet path: pod → veth → bridge → encap → NIC → other node → decap → pod

### 4. AWS VPC CNI (EKS-specific)
- Each pod gets a secondary ENI IP from VPC
- No overlay — native VPC routing performance
- IP exhaustion: max pods per node = max ENI IPs
- IPAMD daemon manages IP address pool

---

## 🔗 Docs & Resources

- [Kubernetes networking model](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
- [AWS VPC CNI](https://github.com/aws/amazon-vpc-cni-k8s)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create two pods on different nodes, ping between them
- [ ] **Lab 2:** Trace the packet path: inspect veth pairs, bridge, routes on the node
- [ ] **Lab 3:** Use tcpdump inside a pod to capture traffic
- [ ] **Lab 4:** Check the pod CIDR assigned to each node: `kubectl get node -o jsonpath`
- [ ] **Lab 5:** On EKS: check ENI assignments with `aws ec2 describe-network-interfaces`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-18:** Pod-to-pod connectivity broken after CNI upgrade — veth pair missing

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. Why does Kubernetes require a flat network (no NAT between pods)?
2. How does same-node pod communication work at the Linux level?
3. What is VXLAN and why is it used for cross-node pod networking?
4. How does AWS VPC CNI differ from overlay networking?
5. What limits the number of pods per node on EKS?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-18
- [ ] Answered interview questions
- [ ] Notes written
