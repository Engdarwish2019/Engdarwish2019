## Hi, I'm Ahmed Darwish 👋

**Senior HPC DevOps Engineer** · Alexandria, Egypt · open to freelance, part-time and full-time remote work

I build and automate the infrastructure that research and AI teams run on: HPC clusters with
Slurm, bare-metal provisioning with xCAT and MAAS, and Kubernetes platforms on AWS, Azure and GCP,
all as code and with security built in.

- 🖥️ **HPC:** Slurm (scheduling, accounting, GPU partitions), xCAT and MAAS provisioning, Ansible at cluster scale
- ☁️ **Cloud & Kubernetes:** AWS, GCP, Azure, DigitalOcean · EKS, GKE, AKS · migrations to Kubernetes
- 🧱 **Infrastructure as code:** Terraform, Ansible, GitOps with Argo CD
- 🔐 **DevSecOps:** secure CI/CD, policy as code, image signing, secrets management
- 👥 Led a DevOps team: CI/CD standards, IaC and container best practices, mentoring

### Projects

Lab projects and reference implementations. Every repository is validated in CI on each push
(see the badge in each README); deploying them creates billable cloud resources.

| Project | What it shows |
|---|---|
| [slurm-aws-terraform](https://github.com/Engdarwish2019/slurm-aws-terraform) | Slurm cluster on AWS with Terraform: configless Slurm, accounting, EFS, GPU partition, SSM-only access. Self-draining node health checks (ECC, XID, row remapping), NCCL and HPL benchmarks (HPL runs in CI), EC2 auto-recovery and alerting |
| [ansible-hpc-roles](https://github.com/Engdarwish2019/ansible-hpc-roles) | Ansible roles for EL9 clusters: Slurm, MUNGE, NFS, Lmod, NVIDIA drivers with a DCGM diagnostic gate, hardening and xCAT bare-metal provisioning |
| [slurm-observability](https://github.com/Engdarwish2019/slurm-observability) | Prometheus, Alertmanager and Grafana for Slurm and GPUs, with unit-tested alert rules and DCGM metrics from one host engine per node |
| [multicloud-k8s-terraform](https://github.com/Engdarwish2019/multicloud-k8s-terraform) | One secure Kubernetes baseline on EKS, AKS and GKE with GPU pools, offline `terraform test` suites, GitHub Actions and Azure DevOps pipelines, OIDC only (no stored keys) |
| [platform-gitops](https://github.com/Engdarwish2019/platform-gitops) | Internal developer platform on Argo CD: Kyverno, Crossplane, Backstage, Argo Rollouts canaries, Istio ambient mTLS, External Secrets with Vault, Kueue GPU queues, vLLM on GPUs |
| [devsecops-pipeline](https://github.com/Engdarwish2019/devsecops-pipeline) | Secure supply chain: gitleaks, Semgrep, Trivy, SBOM, ZAP, Cosign keyless signing, SLSA provenance, Vault, Falco, every action pinned to a commit |

### How the projects fit together

```mermaid
flowchart LR
    tf["multicloud-k8s-terraform<br/>EKS · AKS · GKE"] --> k8s[(Kubernetes)]
    gitops["platform-gitops<br/>Argo CD, Kyverno, Istio,<br/>Rollouts, Kueue, vLLM"] --> k8s
    sec["devsecops-pipeline<br/>scan, SBOM, sign"] -- "signed image" --> gitops
    vault[(Vault)] -- "secrets" --> gitops
    sec -. "Vault roles" .-> vault

    slurmtf["slurm-aws-terraform<br/>Slurm on AWS"] --> hpc[(Slurm cluster)]
    ans["ansible-hpc-roles<br/>bare metal / on-prem"] --> hpc
    obs["slurm-observability<br/>Prometheus, Grafana, DCGM"] --> hpc
```

Terraform builds the clusters, Argo CD runs the platform on them, and the DevSecOps pipeline
produces the signed image the platform verifies before admitting it and ships as a canary. On the
HPC side, the same Slurm node health check and GPU monitoring are used on AWS and on bare metal.

### Skills by area

| Area | Where to see it |
|---|---|
| **Kubernetes & Terraform** | Cluster builds on three clouds, Terraform modules with offline tests, Kubernetes manifests validated against their schemas in CI |
| **Multi-cloud** | AWS (VPC, EKS, EFS, KMS, SSM, CloudWatch, EventBridge), Azure (AKS, Entra ID, workload identity), GCP (GKE, Binary Authorization, Workload Identity); GitHub Actions and Azure DevOps with OIDC |
| **Platform engineering** | Argo CD app of apps, Argo Rollouts with Prometheus analysis, Crossplane self-service APIs, Kyverno policies with tests, Backstage golden path, Prometheus and OpenTelemetry |
| **DevSecOps** | SAST, DAST, image and IaC scanning, SBOM, Cosign and SLSA provenance, Vault (Agent injector and External Secrets), Falco, Istio mTLS, NetworkPolicies, pinned supply chain |
| **HPC / AI infrastructure** | Slurm, Ansible, xCAT, NVIDIA drivers and DCGM, NCCL tests, HPL, GPU node health, vLLM serving, Kueue GPU quotas |

### Tech stack

![Slurm](https://img.shields.io/badge/Slurm-0B5394?style=flat-square)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo%20CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Istio](https://img.shields.io/badge/Istio-466BB0?style=flat-square&logo=istio&logoColor=white)
![Vault](https://img.shields.io/badge/Vault-FFEC6E?style=flat-square&logo=vault&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Azure DevOps](https://img.shields.io/badge/Azure%20DevOps-0078D7?style=flat-square&logo=azuredevops&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![NVIDIA](https://img.shields.io/badge/NVIDIA%20GPU-76B900?style=flat-square&logo=nvidia&logoColor=white)

### Focus for 2026–2027

Kubernetes administration and security (CKA, then CKS), platform engineering (Argo CD,
Crossplane, Backstage) and GPU / AI infrastructure (NVIDIA AI Operations and AI Infrastructure).

### Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Ahmed%20Darwish-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/ahmed-darwish-0b4070166)
