# Senior Platform Engineer Topics Map

## What is this file

To ingress in the market, I take the what a Senior Platform Engineer do in real prod. Only the information that's show in his LinkedIn! I now the tools he use now is too much, because I have to understand the basics, but send this to an IA, it give me some useful topics for the future, and I’ll put this on record here for the future. (I know things might change in the future.)

## Goal

Map real senior platform engineering topics to this homelab without copying enterprise complexity too early.

## Useful Topics From The Reference

The senior platform engineer experience mentioned these areas:

- AWS infrastructure with Terraform and Terragrunt.
- VPC design focused on high availability and security.
- Secrets management with HashiCorp Vault.
- CI/CD pipelines with GitLab.
- Kubernetes deployments with GitOps and Argo CD.
- Infrastructure monitoring.
- AWS Organizations and multi-account environments.
- Cross-cluster service mesh with Istio.
- OpenSearch operations.
- Apache Airflow operations across EKS clusters.

## How This Maps To The Homelab

| Enterprise Topic | Homelab Equivalent | When To Study |
| --- | --- | --- |
| AWS VPC | Home network, subnets, gateway, firewall | Now |
| Terraform | Provisioning cloud resources or local lab resources | After Linux/network basics |
| Terragrunt | Terraform composition at scale | Much later |
| Vault | Secrets management | After apps and CI/CD |
| GitLab CI | GitHub Actions | During CI/CD phase |
| Kubernetes | k3s | After Docker Compose |
| Argo CD | GitOps for k3s | After basic Kubernetes |
| Monitoring | Uptime Kuma, Prometheus, Grafana | After first services |
| AWS Organizations | Multi-account cloud governance | Much later |
| Istio | Service mesh | Much later |
| OpenSearch | Search/log analytics | Only with a real use case |
| Airflow | Workflow orchestration | Only with a real data/workflow use case |

## Brutally Honest Assessment

Most of these topics are valuable, but they are not all useful at the beginning.

The right sequence is:

1. Understand Linux, networking, SSH, firewall, DNS, and logs.
2. Deploy real services manually.
3. Containerize them.
4. Automate deploys.
5. Add monitoring.
6. Add infrastructure automation.
7. Then study Kubernetes and GitOps.
8. Only then touch service mesh, Vault, multi-account cloud, OpenSearch, or Airflow.

## What To Avoid

- Installing Vault before having real secrets to manage.
- Installing Kubernetes before understanding containers and reverse proxies.
- Installing Istio before understanding Kubernetes networking.
- Installing OpenSearch just because it sounds enterprise.
- Using Terraform before knowing what infrastructure you are trying to manage.

