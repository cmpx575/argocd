# ArgoCD GitOps Repository

This repository implements the App-of-Apps pattern for ArgoCD on OCI OKE (Oracle Kubernetes Engine).

## Repository Structure

- **infra/**: Infrastructure components deployed as Helm charts
  - cert-manager: Certificate management
  - cilium: Networking and security
  - grafana: Monitoring and visualization
  - cloudnativepg: Cloud Native PostgreSQL operator

- **apps/**: Application deployments for multiple environments
  - **app1/**: Application 1 microservices
    - instagram-service-api: Bun/Hono API service (dev, qa, prod)
    - gemini-service-api: Python FastAPI service (dev, qa, prod)
    - supabase: Supabase database service (dev, qa, prod)
  - **app2/**: Application 2 microservices
    - instagram-service-api: Bun/Hono API service (dev, qa, prod)
    - gemini-service-api: Python FastAPI service (dev, qa, prod)
    - supabase: Supabase database service (dev, qa, prod)

## Environment Setup

All applications follow the standard GitOps deployment pattern with three environments:
- **dev**: Development environment
- **qa**: Quality Assurance environment
- **prod**: Production environment

## How It Works

The `root-app.yaml` Application CR references all ArgoCD Applications in this repository, implementing the App-of-Apps pattern. It automatically syncs any changes to the infrastructure or application configurations to the Kubernetes cluster.
# argocd
