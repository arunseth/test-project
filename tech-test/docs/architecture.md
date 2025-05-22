# Microservice CI/CD on AWS with Jenkins and Kubernetes


# Architecture Overview

## Considerations
- Modular Kubernetes YAMLs for deployment, configuration, ingress, and secrets.
- Helm chart templating for flexibility across environments.
- Jenkins pipeline handles CI/CD with automated tests, linting, Docker builds, Helm deployment, and notifications.
- Infrastructure provisioned via Terraform (EKS + ECR).

## CI/CD Workflow
1. Code pushed to GitHub triggers Jenkins
2. Linting with yamllint and kubeval
3. Run unit tests (mocked for simplicity)
4. Build and push Docker image to ECR
5. Deploy to EKS using Helm
6. Slack notifications on success/failure

## AWS Infrastructure
- EKS created via Terraform using aws-eks module
- ECR repository provisioned for Docker image storage
- IAM Roles required:
  - EKS Cluster IAM role (control plane)
  - Node Group IAM role (worker nodes)
  - Jenkins IAM role with permissions:
    - `eks:DescribeCluster`
    - `ecr:GetAuthorizationToken`
    - `ecr:BatchCheckLayerAvailability`
    - `ecr:PutImage`
    - `ecr:InitiateLayerUpload`
    - `ecr:UploadLayerPart`
    - `ecr:CompleteLayerUpload`

## Long-term Maintenance
- Set up Prometheus/Grafana for monitoring EKS
- Use External Secrets Operator or AWS Secrets Manager
- Use IRSA for Pod-level IAM permissions
- Add Helm values validation or schema
- Implement Blue/Green or Canary deployments with Argo Rollouts

