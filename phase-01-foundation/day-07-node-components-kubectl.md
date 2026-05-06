# Day 07 — Node Components + kubectl Mastery

> **Phase:** 1 — Foundation | **Week:** Week 1 | **Time:** 3–4 hours

---

## 📚 Topics to Study

### 1. kubelet Deep Dive
- Node registration with API server
- Pod lifecycle management: create, start, monitor, stop
- Pod spec sources: API server watch + static pod manifests
- PLEG: Pod Lifecycle Event Generator
- kubelet config file: /var/lib/kubelet/config.yaml
- Node status reporting: conditions, allocatable resources

### 2. kube-proxy
- iptables mode: DNAT rules, conntrack, performance at scale
- IPVS mode: kernel hash table, better for >1000 services
- How ClusterIP is implemented (it's not a real IP)
- Endpoint slices vs Endpoints

### 3. kubectl — Power User Commands
- get, describe, apply, delete, edit, patch
- exec, logs, port-forward, cp, top
- --dry-run=client vs --dry-run=server
- kubectl explain <resource>.<field>

### 4. kubectl Output Tricks (CKA Speed)
- jsonpath: -o jsonpath='{.items[*].metadata.name}'
- custom-columns: -o custom-columns=NAME:.metadata.name
- kubectl get pods -A (all namespaces)
- kubectl get events --sort-by=.lastTimestamp
- -w flag: watch for changes

---

## 🔗 Docs & Resources

- [kubelet config](https://kubernetes.io/docs/reference/config-api/kubelet-config.v1beta1/)
- [kubectl cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- [kube-proxy modes](https://kubernetes.io/docs/reference/networking/virtual-ips/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Run 10 essential kubectl commands from the cheatsheet
- [ ] **Lab 2:** Use jsonpath to extract all pod IPs in default namespace
- [ ] **Lab 3:** Use custom-columns to show pod name + node + status in one line
- [ ] **Lab 4:** Watch events in real time while creating a deployment
- [ ] **Lab 5:** Use `kubectl explain pod.spec.containers.resources` to explore the schema
- [ ] **Lab 6:** Switch between contexts: create two kind clusters, switch kubeconfig context

---

## 🐛 Production Issue to Debug
> After labs

- **PI-05:** Node NotReady — kubelet certificate expired, how to renew and rejoin

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the PLEG and what happens when it gets stuck?
2. What is the difference between iptables mode and IPVS mode in kube-proxy?
3. How does `kubectl exec` work under the hood?
4. What does `kubectl apply` do differently from `kubectl create`?
5. How do you quickly extract data from kubectl output in a CKA exam?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-05
- [ ] Answered interview questions
- [ ] Notes written
