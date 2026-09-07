# Homelab Platform

A hands-on platform engineering lab built on an Ubuntu Server.

## Goal

Build a small production-like environment to learn Linux, networking, secure access, deployments, automation, observability, CI/CD, containers, and eventually Kubernetes.

This is not a tool showcase. Every component should solve a real operational problem.

## Principles

- Version everything that can be versioned.
- Turn manual changes into documentation first, then automation.
- Make it work, understand it, then automate it.
- Every tool must have a clear reason to exist.
- A backup only counts after a restore has been tested.
- Prefer boring, reliable infrastructure before complex platforms.

## Target Architecture (not built yet)

Nothing below exists on the server today. This is the destination, not the
current state. See `docs/roadmap.md` for what is actually done.

```text
Mac
  -> SSH
Ubuntu Server
  -> Nginx
  -> Docker Compose
  -> Apps
  -> Postgres
  -> Prometheus
  -> Grafana
  -> Uptime Kuma
```

## Learning Path

1. Linux and network foundation.
2. Secure SSH and operational access.
3. Nginx and the first service.
4. Docker Compose with app and database.
5. CI/CD with GitHub Actions.
6. Observability with Prometheus, Grafana, and Uptime Kuma.
7. Automation with Ansible.
8. Backups and tested restores.
9. Lightweight Kubernetes with k3s.
10. Advanced platform topics when the basics are solid.

## Repository Structure

```text
docs/decisions/    Architecture decision records (ADRs)
docs/runbooks/     Operational step-by-step guides
docs/references/   External references and study notes
docs/inventory.md  Factual state of the server and network
docs/roadmap.md    Active phases (0-2)
docs/backlog.md    Future phases, not planned in detail yet
docs/learning      Notes about everthing
```

## Current Status

See [docs/roadmap.md](docs/roadmap.md).
