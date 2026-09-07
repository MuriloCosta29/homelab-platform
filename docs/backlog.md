## Phase 3: Firewall And Base System

- [ ] Configure `ufw`.
- [ ] Allow only required ports.
- [ ] Configure timezone.
- [ ] Update packages.
- [ ] Configure an operational user.
- [ ] Document essential commands.

## Phase 4: First Service

- [ ] Install Nginx.
- [ ] Serve a static page.
- [ ] Access it from the Mac browser.
- [ ] Configure a reverse proxy for a simple app.
- [ ] Document the runbook.

## Phase 5: Docker Compose

- [ ] Install Docker.
- [ ] Install Docker Compose.
- [ ] Create a stack with app + Postgres.
- [ ] Configure volumes.
- [ ] Configure healthchecks.
- [ ] Configure logs.

## Phase 6: CI/CD

- [ ] Create a test workflow.
- [ ] Build a Docker image.
- [ ] Publish the image to GHCR.
- [ ] Deploy to the server over SSH.
- [ ] Create a simple rollback procedure.

## Phase 7: Observability

- [ ] Install Uptime Kuma.
- [ ] Install Prometheus.
- [ ] Install Grafana.
- [ ] Monitor CPU, RAM, disk, and services.
- [ ] Create a simple alert.

## Phase 8: Automation

- [ ] Create an Ansible inventory.
- [ ] Automate users, packages, and firewall.
- [ ] Automate Docker.
- [ ] Automate Nginx.
- [ ] Rebuild the server from scratch with a playbook.

## Phase 9: Backups

- [ ] Automate Postgres backups.
- [ ] Back up important volumes.
- [ ] Store backups outside the server.
- [ ] Test restore.
- [ ] Document simple RTO/RPO expectations.

## Phase 10: Kubernetes

- [ ] Install k3s.
- [ ] Deploy the first workload.
- [ ] Configure ingress.
- [ ] Configure volumes.
- [ ] Configure cert-manager if a real domain is available.
- [ ] Migrate one app from Compose to k3s.

## Phase 11: Advanced Platform Topics

- [ ] Study Terraform with a small local or cloud experiment.
- [ ] Study GitOps with Argo CD.
- [ ] Study secret management with Vault or a simpler alternative first.
- [ ] Study multi-environment infrastructure.
- [ ] Study service mesh only after Kubernetes networking is understood.
- [ ] Study OpenSearch and Airflow only if there is a real use case.

