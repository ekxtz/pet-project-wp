# pet-project-wp


# AWS EKS + WordPress High Availability Project

Это проект по развертыванию отказоустойчивой архитектуры WordPress в облаке AWS с использованием Terraform и Kubernetes.

## 🏗 Архитектура

Проект реализует современный стек технологий с фокусом на безопасность и экономию средств:

* **Networking:** VPC с публичными и приватными подсетями.
* **Load Balancing:** AWS Application Load Balancer (ALB) + Nginx Ingress Controller.
* **Compute:** AWS EKS (Kubernetes) на базе **Spot-инстансов (t3.medium)** для экономии бюджета до 70%.
* **Database:** Managed AWS RDS (MySQL 8.0) в изолированной приватной сети.
* **Storage:** AWS S3 для статических файлов WordPress.


-------------------
🛠 Технологии

    Infrastructure as Code: Terraform

    Cloud Provider: AWS

    Orchestration: Kubernetes (EKS)

    Database: RDS MySQL

    CI/CD Ready: Структура подготовлена для автоматизации через GitHub Actions.

📂 Структура проекта

    terraform/: Код инфраструктуры, разбитый на модули (VPC, EKS, RDS, S3).

    k8s/: Манифесты Kubernetes (Deployments, Services, Ingress).

    terraform/providers.tf: Настройка AWS и удаленного S3 Backend для хранения стейта.



    --------------
### Визуализация схемы:

```text
Project: Pet-Project-wp
│
├── VPC (Virtual Private Cloud) 
│   ├── Public Subnet (ALB) 
│   └── Private Subnet (EKS Nodes & RDS)
│
├── EKS Cluster (Control Plane)
│   ├── Managed Node Group (Spot t3.medium)
│   │   ├── Node A [Pod 1, Pod 2]
│   │   └── Node B [Pod 3]
│   └── K8s Services [Nginx Ingress]
│
└── Managed Services
    ├── RDS Instance [MySQL Engine]
    └── S3 Bucket [Media Storage]


--------------------------------------
доп информация визуализация параметров
-----------------------------------------

 project

├── AWS Application Load Balance + Nginx Ingress


│ ├── AWS EKS (Kubernetes)
K8s Deployment (3 Replicas)
                ├── 

                 ├── Node A: Pod 1  2 vCPU / 4GB RAM, Pod 2  2 vCPU / 4GB RAM Spot instances -
 t3.medium

│ ├── 
Node B: Pod 3
2 vCPU / 4GB RAM Spot instances -t3.medium

├── AWS S3 gp3 20GB

├── AWS RDS 2 vCPU / 4GB RAM db.t3.medium

               ├── MySQL

