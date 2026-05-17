# Production Project 01 — 3-Tier Application on EKS with Full Networking

> **Type:** Production Project | **Platform:** AWS EKS

---

## 🎯 Goal

Deploy a production-ready 3-tier application (React + Node.js API + PostgreSQL) on EKS with complete networking: Ingress, TLS, DNS, NetworkPolicy, and ExternalDNS.

---

## 🏗️ Architecture

- EKS cluster (eksctl) — 2 AZs, managed node groups
- Frontend: React app as Deployment + ClusterIP Service
- Backend: Node.js API as Deployment + ClusterIP Service
- PostgreSQL: StatefulSet + Headless Service + EBS PVC
- NGINX Ingress Controller + LoadBalancer Service
- cert-manager with Let's Encrypt (or self-signed for lab)
- ExternalDNS → Route53 (or /etc/hosts for lab)
- NetworkPolicy: zero-trust between tiers

---

## 📋 Build Phases

### Phase 1: Cluster Setup
- [ ] Create EKS cluster with eksctl (or kind for local)
- [ ] Install AWS VPC CNI + Calico for NetworkPolicy
- [ ] Install NGINX Ingress Controller via Helm
- [ ] Install cert-manager via Helm
- [ ] Deploy ExternalDNS with IRSA

### Phase 2: Application Deployment
- [ ] Deploy PostgreSQL StatefulSet with EBS PVC
- [ ] Deploy Backend API as Deployment, connect to PostgreSQL
- [ ] Deploy Frontend as Deployment, connect to Backend
- [ ] Verify app works end-to-end via ClusterIP services

### Phase 3: Networking Layer
- [ ] Create Ingress: api.yourdomain.com → backend, app.yourdomain.com → frontend
- [ ] Configure TLS with cert-manager annotation
- [ ] Verify ExternalDNS creates Route53 records
- [ ] Apply default-deny NetworkPolicy to app namespace
- [ ] Allow: frontend → backend (port 3000)
- [ ] Allow: backend → postgres (port 5432)
- [ ] Verify: frontend cannot reach postgres directly

### Phase 4: Validation
- [ ] Access frontend via HTTPS domain
- [ ] Verify TLS certificate is valid
- [ ] Test NetworkPolicy isolation
- [ ] Check ExternalDNS records in Route53

---

## 🐛 Inject & Debug (after full build)

- [ ] PI-20: Break the backend Service selector — 502 on Ingress, debug
- [ ] PI-22: Delete CoreDNS pods — observe DNS failure, restore
- [ ] PI-26: Apply wrong NetworkPolicy — block frontend→backend, debug and fix
- [ ] PI-23: Bad Ingress annotation — routing breaks, fix annotation

---

## ✅ Done When

- [ ] Frontend accessible at HTTPS domain
- [ ] TLS certificate valid and auto-renewed
- [ ] All 4 injected issues debugged and resolved
- [ ] NetworkPolicy correctly isolates tiers
- [ ] ExternalDNS manages DNS automatically
