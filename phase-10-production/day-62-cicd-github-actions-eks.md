# Day 62 — CI/CD with GitHub Actions + EKS

> **Phase:** 10 — Production | **Week:** Week 12 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. CI/CD Pipeline Design
- CI: test → lint → build image → scan → push to ECR
- CD: update image tag → deploy to cluster
- Environment promotion: dev → staging → prod (manual approval for prod)
- Image tagging: git SHA for traceability, semver for releases

### 2. GitHub Actions for EKS
- OIDC federation: no stored AWS keys in GitHub secrets
- aws-actions/configure-aws-credentials: OIDC-based auth
- aws-actions/amazon-ecr-login: authenticate to ECR
- Deployment: kubectl apply or helm upgrade

### 3. Security Best Practices
- OIDC instead of long-lived AWS access keys
- Pin action versions to specific SHAs
- Use Trivy in CI to block HIGH CVE images
- Sign images with Cosign after build
- Store no secrets in GitHub — use Secrets Manager

### 4. Deployment Verification
- kubectl rollout status: wait for rollout to complete
- Smoke test: curl the health endpoint post-deploy
- Automatic rollback: if smoke test fails, helm rollback

---

## 🔗 Docs & Resources

- [GitHub Actions](https://docs.github.com/en/actions)
- [OIDC with AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)
- [amazon-ecr-login action](https://github.com/aws-actions/amazon-ecr-login)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Create GitHub Actions workflow: test → build → push to ECR
- [ ] **Lab 2:** Set up OIDC federation: GitHub → AWS (no stored keys)
- [ ] **Lab 3:** Add Trivy scanning step: fail on HIGH severity
- [ ] **Lab 4:** Add Cosign signing step
- [ ] **Lab 5:** Add deployment step: helm upgrade to EKS dev environment
- [ ] **Lab 6:** Add rollout verification: kubectl rollout status with timeout
- [ ] **Lab 7:** Add manual approval gate before prod deployment

---

## 🐛 Production Issue to Debug
> After labs

- **PI-60:** CI pipeline deploying bad image to prod — no scan gate and no smoke test

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. How does GitHub Actions OIDC authentication with AWS work?
2. What are the stages of a good K8s CI/CD pipeline?
3. How do you implement a deployment gate (wait for rollout)?
4. Why should you use git SHA as image tag?
5. How do you implement manual approval for production in GitHub Actions?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 7 labs
- [ ] Debugged PI-60
- [ ] Answered interview questions
- [ ] Notes written
