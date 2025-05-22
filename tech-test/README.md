# Senior DevOps Engineer Tech Test (GitHub + Jenkins + AWS)
Welcome! This tech test is designed to simulate real-world tasks you'd
face at Cartrawler. We use GitHub, Jenkins, and AWS (especially EKS and
ECR) for our DevOps stack.
---
## 🧪 Your Mission
Build and deploy a simple microservice using Jenkins and Kubernetes on
AWS. Follow the instructions below and feel free to enhance wherever you
see fit!
---
### 🔧 Part 1: Kubernetes Setup
- Use the provided app or create your own (keep it simple)
- Define the following K8s manifests in `/k8s`:
 - `deployment.yaml`
 - `service.yaml`
 - `ingress.yaml`
 - `configmap.yaml`/ `secret.yaml`
 - Package with Helm library chart in `/helm-chart`
### ⚙Part 2: Jenkins Pipeline
- Create a `Jenkinsfile` that does:
 1. Checkout
 2. Lint YAML/K8s (e.g., kubeval/yamllint)
 3. Run mocked unit tests
 4. Build and push Docker image to Amazon ECR
 5. Deploy the k8s resources to EKS in jenkins namespace
 6. Notify via Slack/email
 7. Optional: rollback on deploy failure
- Include separate pipelines or stages for `staging` and `production`
> ⚠**Note:** If you do not have access to ECR or EKS, you may:
> - Comment out the related steps in the Jenkinsfile
> - Add `echo` statements or `sleep` to simulate those stages
> - Clearly document what would happen at each step
### ☁Part 3: AWS
> ⚠**Note:** If you do not have access to a live AWS environment
(EKS/ECR), that's completely fine.
>
> - Please document how you would structure and implement these steps,
assuming full access.
> - You may use mock values or simulate with tools like `minikube`,
`kind`, or Docker locally.
> - The goal is to see your DevOps thinking and approach — infrastructure
doesn't need to be live.
- Use AWS CLI to interact with ECR and EKS (can be commented/mocked if no
access)
- Document IAM roles/permissions required
- Bonus: suggest or include infra-as-code (e.g., Terraform/CDK) for EKS
cluster
### 🧠 Part 4: Documentation
Document your solution in the `docs/archtiecture.md` file:
- Considerations in your approach
- How you would implement the solution in an existing organisation
- Additional things you would consider for long term maintenance
---
## ✅ Submission
- Push your code to a public GitHub repo or share a ZIP file
- Include a short `README` with setup steps
- Make sure everything is runnable and well-commented
