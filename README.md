# Platform Jenkins

Infrastructure as Code (IaC) project for provisioning and configuring a Jenkins CI/CD platform using Terraform, Ansible, Docker, and AWS.

## Overview

Platform Jenkins automates the deployment and configuration of a Jenkins environment consisting of a Jenkins controller and AWS-based build agents.

The project uses Terraform to provision Jenkins agent infrastructure on AWS and Ansible to configure Jenkins controllers and agents with the required tools for software delivery workflows, including Docker, Maven, and Kubernetes CLI utilities.

## Architecture

```text
                    Jenkins Controller
                   (Docker Container)
                           │
                           │ SSH Agent Connection
                           ▼
                 Jenkins Agent (AWS EC2)
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       Maven           Docker          kubectl
      Build Tool    Container Build   Kubernetes
```

## Features

### Infrastructure Provisioning

* AWS EC2 provisioning with Terraform
* Configurable instance types and AMIs
* Infrastructure lifecycle management through Infrastructure as Code

### Jenkins Automation

* Automated Jenkins controller deployment
* Jenkins deployment using Docker Compose
* Automated plugin installation and configuration
* Jenkins health verification and initialization

### Build Agent Configuration

* Automated Jenkins agent setup with Ansible
* Java OpenJDK installation
* Maven installation for application builds
* Docker installation for container image creation
* kubectl installation for Kubernetes deployments

### CI/CD Platform Enablement

* Git integration support
* Pipeline execution support
* Container image build capabilities
* Kubernetes deployment tooling
* Distributed build execution through Jenkins agents

## Technology Stack

| Category                 | Technology     |
| ------------------------ | -------------- |
| CI/CD Platform           | Jenkins        |
| Infrastructure as Code   | Terraform      |
| Configuration Management | Ansible        |
| Container Runtime        | Docker         |
| Container Orchestration  | Docker Compose |
| Build Tool               | Maven          |
| Kubernetes CLI           | kubectl        |
| Cloud Platform           | AWS            |
| Operating System         | Ubuntu Linux   |
| Runtime                  | OpenJDK 21     |

## Repository Structure

```text
platform-jenkins/
├── terraform/
│   ├── main.tf
│   ├── provider.tf
│   ├── variables.tf
│   ├── versions.tf
│   └── output.tf
│
├── ansible/
│   ├── inventory.ini
│   ├── jenkins_setup.yaml
│   ├── jenkins_agent_setup.yaml
│   └── files/
│       └── docker-compose.yml
│
└── README.md
```

## Deployment Workflow

### 1. Provision AWS Infrastructure

```bash
cd terraform

terraform init
terraform plan
terraform apply
```

### 2. Configure Jenkins Environment

```bash
cd ansible

ansible-playbook jenkins_setup.yaml

ansible-playbook jenkins_agent_setup.yaml
```

### 3. Access Jenkins

```text
http://<jenkins-controller-ip>:8080
```

## Deployment Flow

1. Terraform provisions Jenkins agent infrastructure on AWS.
2. Ansible configures the Jenkins controller host.
3. Docker and Docker Compose are installed.
4. Jenkins is deployed as a containerized service.
5. Required Jenkins plugins are installed.
6. Jenkins agents are configured with Java, Maven, Docker, and kubectl.
7. Agents connect to the Jenkins controller.
8. The CI/CD platform becomes ready for build and deployment workloads.

## Jenkins Components

### Jenkins Controller

* Jenkins LTS deployment
* Docker-based runtime
* Plugin management
* Pipeline orchestration
* Agent management

### Jenkins Agents

* Build execution
* Docker image creation
* Maven-based application builds
* Kubernetes deployment support

## Installed Jenkins Plugins

* Git
* Workflow Aggregator
* Pipeline Stage View
* Credentials Binding
* SSH Build Agent

## Requirements

* AWS Account
* Terraform
* Ansible
* Docker
* SSH Access
* Ubuntu-based Hosts

```
```
