# Day 60 — Network Debugging

> **Phase:** 9 — Troubleshooting | **Week:** Week 11 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. DNS Debugging
- Test from inside pod: nslookup <service>, dig <fqdn>
- Check resolv.conf: cat /etc/resolv.conf in pod
- Check CoreDNS: kubectl logs -n kube-system -l k8s-app=kube-dns
- Common issue: ndots misconfiguration causing extra lookups

### 2. Service Connectivity Debugging
- Does the service have endpoints? kubectl get endpoints <svc>
- Are pod labels matching service selector?
- Can you reach the pod IP directly (bypass service)?
- curl from inside another pod: `kubectl run test --image=curlimages/curl`

### 3. NetworkPolicy Debugging
- Test with netshoot: rich network debugging tools
- Try connecting before/after policy apply
- Check policy selectors match pod labels
- Cilium: cilium monitor — live packet trace

### 4. Ingress Debugging
- Check Ingress controller logs
- Check backend service has endpoints
- curl with Host header: `curl -H 'Host: myapp.com' http://<ingress-ip>`
- Check TLS certificate: openssl s_client

### 5. Essential Debug Images
- nicolaka/netshoot: curl, dig, nslookup, nmap, tcpdump, iperf
- curlimages/curl: minimal curl
- busybox: basic shell tools
- Use with: kubectl run debug --image=nicolaka/netshoot -it --rm

---

## 🔗 Docs & Resources

- [DNS debugging](https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/)
- [netshoot](https://github.com/nicolaka/netshoot)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Debug DNS: nslookup a service from inside a pod
- [ ] **Lab 2:** Debug broken Service: find the selector mismatch and fix it
- [ ] **Lab 3:** Debug NetworkPolicy: use netshoot to trace blocked connections
- [ ] **Lab 4:** Debug Ingress 502: trace from Ingress → Service → Pod
- [ ] **Lab 5:** Use tcpdump inside a pod to capture and analyze traffic

---

## 🐛 Production Issue to Debug
> After labs

- **PI-20:** Service endpoint empty — selector mismatch, full debug trace
- **PI-22:** CoreDNS down — DNS fails for all pods, restore and verify
- **PI-26:** NetworkPolicy blocking traffic — find the blocking rule

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the first 3 steps to debug a service that is unreachable?
2. How do you test DNS from inside a pod?
3. What does an empty endpoints list mean for a Service?
4. How do you debug a NetworkPolicy that is blocking traffic?
5. What is the netshoot image and what tools does it include?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 5 labs
- [ ] Debugged PI-20
- [ ] Debugged PI-22
- [ ] Debugged PI-26
- [ ] Answered interview questions
- [ ] Notes written
