# Day 21 — Services — Complete Guide

> **Phase:** 3 — Networking | **Week:** Week 4 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Why Services Exist
- Pods are ephemeral — IPs change on restart
- Service: stable virtual IP + DNS name + load balancing
- Service selects pods via label selector
- kube-proxy programs iptables/IPVS to forward traffic

### 2. ClusterIP
- Default type — cluster-internal only
- Virtual IP: not assigned to any interface (DNAT via iptables)
- DNS: <service>.<namespace>.svc.cluster.local
- EndpointSlices: list of pod IPs behind the service

### 3. NodePort
- Exposes service on every node's IP at a static port (30000-32767)
- External traffic: NodeIP:NodePort → ClusterIP → Pod
- Not production-ready without a load balancer in front

### 4. LoadBalancer
- Cloud provider creates external load balancer
- On EKS: creates NLB or ALB via cloud-controller-manager
- Annotations control NLB vs ALB, internal vs external

### 5. Headless Service
- clusterIP: None — no virtual IP
- DNS returns individual pod IPs directly
- Required by StatefulSets for stable pod DNS names
- Use case: client-side load balancing, service discovery

### 6. ExternalName
- CNAME alias to an external DNS name
- Use case: migrate external services into cluster namespace
- No proxying — pure DNS CNAME

---

## 🔗 Docs & Resources

- [Services](https://kubernetes.io/docs/concepts/services-networking/service/)
- [EndpointSlices](https://kubernetes.io/docs/concepts/services-networking/endpoint-slices/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create ClusterIP service and verify DNS resolution from inside a pod
- [ ] **Lab 2:** Create NodePort and access from outside the cluster
- [ ] **Lab 3:** On EKS: create LoadBalancer service, verify NLB created in AWS console
- [ ] **Lab 4:** Create Headless service, query DNS and see pod IPs returned
- [ ] **Lab 5:** Create ExternalName service pointing to an external API
- [ ] **Lab 6:** Inspect iptables rules for a service: `iptables -t nat -L | grep <svc-name>`

---

## 🐛 Production Issue to Debug
> After labs

- **PI-20:** Service not routing to pods — endpoint slice empty, selector mismatch debug

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. How does ClusterIP work under the hood (iptables)?
2. What is the difference between ClusterIP, NodePort, and LoadBalancer?
3. When would you use a Headless service?
4. What is an EndpointSlice?
5. How does an ExternalName service work?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-20
- [ ] Answered interview questions
- [ ] Notes written
