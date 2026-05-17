# Day 65 — Service Mesh with Istio

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. Istio Architecture
- Control plane: istiod (Pilot, Citadel, Galley merged)
- Data plane: Envoy sidecar proxied injected into every pod
- istiod manages: config distribution, cert rotation, service discovery

### 2. Mutual TLS (mTLS)
- Automatic mTLS between all services in mesh
- PEER_AUTHENTICATION: mode STRICT = require mTLS
- PeerAuthentication: namespace or mesh-wide policy
- Certificates: rotated automatically by istiod

### 3. Traffic Management
- VirtualService: routing rules (header-based, weight-based)
- DestinationRule: load balancing, circuit breaking, outlier detection
- Gateway: Istio's ingress (replaces Ingress for mesh traffic)
- ServiceEntry: add external services to mesh

### 4. Observability
- Kiali: service dependency graph, traffic visualization
- Distributed tracing: Jaeger integration (automatic span injection)
- Metrics: Envoy reports L7 metrics to Prometheus

### 5. Traffic Shaping
- Canary: VirtualService weight: [90, 10]
- Header-based routing: route beta users to v2
- Fault injection: test resilience by injecting delays/errors
- Circuit breaker: outlierDetection in DestinationRule

---

## 🔗 Docs & Resources

- [Istio docs](https://istio.io/latest/docs/)
- [Istio traffic management](https://istio.io/latest/docs/concepts/traffic-management/)
- [Kiali](https://kiali.io/docs/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Install Istio with istioctl (demo profile)
- [ ] **Lab 2:** Enable sidecar injection in a namespace
- [ ] **Lab 3:** Verify mTLS: use Kiali to see all traffic is mTLS
- [ ] **Lab 4:** Create VirtualService: 90/10 canary between v1 and v2
- [ ] **Lab 5:** Create VirtualService: route requests with header `beta: true` to v2
- [ ] **Lab 6:** Enable circuit breaker: outlierDetection on a service
- [ ] **Lab 7:** Inject a delay fault: 3 second delay to 50% of requests

---

## 🐛 Production Issue to Debug
> After labs

- **PI-63:** Istio sidecar injection breaking app — readiness probe failing with Envoy not ready

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What are the Istio control plane and data plane?
2. How does Istio implement mTLS automatically?
3. What is a VirtualService and how does it differ from a Service?
4. What is a DestinationRule used for?
5. How do you implement circuit breaking with Istio?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-63
- [ ] Answered interview questions
- [ ] Notes written
