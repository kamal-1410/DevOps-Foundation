# DevOps Engineer Interview Prep Roadmap

**Built for a beginner — with practice tests, per-module capstones, and a final mega project**

## Core Principle

Your resume lists Terraform, EKS, Jenkins, Prometheus, IAM, VPC, etc.

The interviewer will ask you to explain these. Your #1 goal is to be able to talk about each item on your resume with a real example, in your own words.

## How the Projects Build

Every module ends with a capstone that you push to GitHub.

Each capstone becomes a piece of the final mega project. By the end you'll have one production-grade portfolio repository that backs every bullet on your resume.

## How to Use This Roadmap

* Spend ~60% of your time doing labs and capstones
* Spend ~40% explaining concepts out loud
* After each module, take the practice test before moving on
* If you cannot pass the test, repeat the module
* Build everything in a free-tier AWS account
* Tear resources down after every lab to avoid charges
* Create one public GitHub repository per capstone
* Include a README explaining:

  * What you built
  * Why you built it
  * Key learnings
* These README files become your interview talking points

### Scoring Rule

Pass only if:

* Conceptual section ≥ 80%
* Hands-on task fully working

---

# Phase 0 — Foundations

Linux, networking, Git, and scripting.

Everything else sits on top of these.

## Learn

### Linux

* Filesystem
* Permissions (`chmod`, `chown`)
* Processes (`ps`, `top`, `kill`)
* `grep`, `sed`, `awk`
* `systemctl`
* Logs

### Networking

* IP/CIDR (`10.0.0.0/16`)
* Ports
* DNS
* HTTP/HTTPS
* TCP vs UDP
* Firewalls

### Git

* Branching
* Merge
* Rebase
* Conflict resolution
* Pull Requests
* `.gitignore`
* Branching strategies

### Bash

* Variables
* Loops
* Conditionals
* Functions
* Exit codes
* Arguments
* Piping

## Practice Test 0

### Conceptual

1. What does `chmod 755 file.sh` mean?
2. Difference between `merge` and `rebase`?
3. What is a `/24` subnet and how many usable hosts does it have?
4. How do you find which process is using port 8080?
5. What is an exit code and why does CI care about it?

### Hands-On

* Write a Bash script that checks whether a service is running.
* Restart the service if it is down.
* Log events with timestamps.
* Create a Git repository.
* Commit the script.
* Create a feature branch.
* Merge back into `main`.

## Capstone 0 — Server Health Sentinel

Build a Bash health-check tool that:

* Monitors CPU
* Monitors memory
* Monitors disk usage
* Monitors a chosen service
* Auto-restarts the service on failure
* Logs results

Deliverables:

* Git repository
* README
* Branching strategy
* Sample log output

---

# Phase 1 — AWS Core

## Services to Master

| Service    | Must Be Able To Explain                                                        |
| ---------- | ------------------------------------------------------------------------------ |
| EC2        | Instances, AMIs, instance types, key pairs, user data                          |
| VPC        | Public/private subnets, route tables, IGW, NAT Gateway, Security Groups, NACLs |
| IAM        | Users, roles, policies, least privilege                                        |
| S3         | Buckets, storage classes, versioning, bucket policies                          |
| RDS        | Managed databases, Multi-AZ, read replicas, backups                            |
| ALB        | Target groups, listeners, health checks                                        |
| Route53    | DNS and routing policies                                                       |
| CloudWatch | Metrics, logs, alarms, dashboards                                              |

## Practice Test 1

### Conceptual

1. Security Group vs NACL?
2. How does EC2 access S3 without keys?
3. What makes a subnet public?
4. When would you use a NAT Gateway?
5. What is least privilege?

### Hands-On

Build:

* VPC
* Public subnet
* Private subnet
* EC2 web server
* Application Load Balancer
* RDS instance

Verify traffic flows correctly.

Tear everything down afterward.

## Capstone 1 — Manual 3-Tier Web App

Architecture:

VPC → ALB → EC2 → RDS

Deliverables:

* Manual AWS deployment
* Architecture diagram
* Documentation

---

# Phase 2 — Infrastructure as Code (Terraform)

## Learn

### Terraform Basics

* `init`
* `plan`
* `apply`
* `destroy`
* Providers
* Resources
* Variables
* Outputs
* Data Sources

### State Management

* Terraform state
* State locking
* State corruption risks

### Backend

* S3 remote backend
* DynamoDB locking

### Advanced

* Modules
* Reusability
* Workspaces
* Dev / Stage / Prod environments

## Practice Test 2

### Conceptual

1. What is Terraform state?
2. Why lock state?
3. Why use modules?
4. Terraform vs CloudFormation?
5. Where should secrets be stored?

### Hands-On

Rebuild Capstone 1 using Terraform.

Requirements:

* Networking module
* Compute module
* S3 backend
* DynamoDB locking

## Capstone 2 — Infrastructure as Code Stack

Deliver:

* Fully reproducible 3-tier application
* Modular Terraform code
* Remote state backend
* State locking

---

# Phase 3 — Containers (Docker)

## Learn

* Images vs Containers
* Dockerfile
* Layers
* Build / Run / Exec / Logs
* Docker Hub
* ECR
* Volumes
* Networks
* Environment Variables
* Multi-stage builds
* Docker Compose

## Practice Test 3

### Conceptual

1. Image vs Container?
2. How do you reduce image size?
3. What is a multi-stage build?
4. Where should secrets live?
5. Explain each Dockerfile instruction.

### Hands-On

* Build a multi-stage Docker image
* Run locally
* Push to ECR

## Capstone 3 — Containerized App + ECR

Deliver:

* Sample application
* Multi-stage Dockerfile
* Docker Compose
* ECR deployment

---

# Phase 4 — Kubernetes (EKS)

## Learn

### Core Components

* Control Plane
* Nodes
* Kubelet

### Kubernetes Objects

* Pod
* Deployment
* ReplicaSet
* Service
* ConfigMap
* Secret
* Namespace
* Ingress

### Commands

* `kubectl get`
* `kubectl describe`
* `kubectl logs`
* `kubectl apply`
* `kubectl exec`

### Advanced

* Rolling Updates
* Rollbacks
* HPA
* Liveness Probes
* Readiness Probes
* IRSA

## Practice Test 4

### Conceptual

1. Pod vs Deployment vs Service?
2. How do rolling updates work?
3. How do you debug CrashLoopBackOff?
4. Liveness vs Readiness?
5. Service type LoadBalancer?

### Hands-On

Deploy your Docker image:

* Minikube/Kind
* Then EKS
* Rolling update
* Rollback

## Capstone 4 — App on EKS

Deliver:

* Deployment
* Service
* ConfigMap
* Secret
* Health probes
* Rolling update demo
* Rollback demo

---

# Phase 5 — CI/CD

## Learn

### Pipeline Flow

Checkout → Build → Test → SonarQube → Trivy → Push → Deploy

### Jenkins

* Jenkinsfile
* Agents
* Credentials
* Triggers

### GitHub Actions

* Workflows
* Jobs
* Steps
* Secrets

### Concepts

* Artifacts
* Promotion
* Approval Gates
* Rollback

## Practice Test 5

### Conceptual

1. Explain an entire CI/CD pipeline.
2. SonarQube vs Trivy?
3. Delivery vs Deployment?
4. Secret management?
5. Failed deployment handling?

### Hands-On

Build a pipeline:

* Build Docker image
* Run Trivy
* Push to ECR
* Deploy to EKS
* Block deployment if tests fail

## Capstone 5 — Automated Pipeline

Deliver:

* Git Push → Production deployment
* Security gates
* Quality gates
* Rollback path

---

# Phase 6 — Monitoring & Logging

## Learn

### Three Pillars

* Metrics
* Logs
* Traces

### Tools

* Prometheus
* Grafana
* CloudWatch

### Reliability

* SLI
* SLO
* SLA
* MTTR
* Self-healing

## Practice Test 6

### Conceptual

1. Monitor a service from scratch.
2. SLO vs SLA?
3. Self-healing example?
4. What is MTTR?
5. Justifying 99.9% uptime?

### Hands-On

* Deploy Prometheus
* Deploy Grafana
* Monitor application
* Create dashboard
* Create alert

## Capstone 6 — Observability Stack

Deliver:

* Prometheus
* Grafana
* Dashboard
* Alert
* Self-healing action

---

# Phase 7 — Configuration Management & Security

## Learn

### Ansible

* Playbooks
* Inventory
* Idempotency

### Security

* Least privilege IAM
* Secrets management
* Image scanning
* Shift-left security

### Cost Optimization

* Right-sizing
* Resource cleanup

## Practice Test 7

### Conceptual

1. What makes Ansible idempotent?
2. Three ways to protect secrets?
3. What is shift-left security?
4. Reducing AWS costs?
5. IAM Roles vs Access Keys?

### Hands-On

Build an Ansible playbook:

* Install packages
* Configure services
* Demonstrate idempotency

## Capstone 7 — Hardening & Config

Deliver:

* Ansible playbook
* IAM policies
* Security documentation

---

# Final Mega Project — Cloud-Native Deployment Platform

## What You Build

A production-grade platform consisting of:

* Terraform infrastructure
* S3 backend
* DynamoDB locking
* Dockerized application
* Amazon EKS deployment
* Jenkins/GitHub Actions pipeline
* SonarQube
* Trivy
* Amazon ECR
* Prometheus
* Grafana
* Ansible
* IAM security
* Health-check tooling

## Requirements Checklist

* Terraform builds everything
* App containerized with multi-stage Dockerfile
* Image stored in ECR
* Runs on EKS
* Rolling updates and rollbacks
* Automated CI/CD
* Security scanning
* Monitoring dashboards
* Self-healing alerts
* Least-privilege IAM
* Clean `terraform destroy`

## Stretch Goals

* Blue/Green deployments
* Canary deployments
* Multiple environments
* Cost optimization reporting

---

# Mega Project Defense Questions

1. Walk through Git push → Production.
2. Why lock Terraform state?
3. Where does security scanning happen?
4. How do you achieve zero-downtime deployments?
5. How do you know the application is healthy?
6. How would you scale for 10× traffic?

---

# Suggested Schedule

| Week | Modules         | Deliverable               |
| ---- | --------------- | ------------------------- |
| 1    | Phase 0–1       | Capstones 0 & 1           |
| 2    | Phase 2–3       | Capstones 2 & 3           |
| 3    | Phase 4–5       | Capstones 4 & 5           |
| 4    | Phase 6–7       | Capstones 6 & 7           |
| 5    | Mega Project    | Integrated platform       |
| 6    | Mock Interviews | STAR + scenario + defense |

---

# Behavioral Preparation (STAR Stories)

Prepare stories for:

* Automation impact
* Production incident handling
* Team disagreement
* Learning a new tool quickly
* Employment gap (2016–2021)

---

# Free Resources

* AWS Skill Builder
* AWS Documentation
* HashiCorp Learn
* Kubernetes.io Tutorials
* Minikube
* Kind
* KodeKloud
* FreeCodeCamp DevOps Videos

---

# Final Reminder

The fastest way to fail a DevOps interview is to list a tool and then go blank when asked about it.

Every capstone exists so every resume bullet has a real story behind it.

**Build the projects. Write the READMEs. Rehearse the defenses.**
