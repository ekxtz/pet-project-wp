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
