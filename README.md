# Doctor Clinic DevOps System

A Laravel-based clinic management and appointment booking platform with a complete DevOps delivery layer.

**Live Application:** http://51.158.200.127:8080

---

## Project Overview

The Doctor Clinic DevOps System supports three user roles in a unified web platform:

| Role | Capabilities |
|------|-------------|
| Patient | Register, browse doctors and specialties, book appointments, patient dashboard |
| Doctor | Manage profile, availability, appointments, doctor dashboard |
| Admin | Manage users, specialties, reports, settings, pages, approvals |

---

## Technology Stack

| Layer | Technologies |
|-------|-------------|
| Application | Laravel 12, PHP 8.2, Blade, Tailwind CSS, Alpine.js, Vite |
| Database | MySQL 5.7 |
| Containerization | Docker CE, Docker Compose v2, Nginx Alpine |
| CI/CD | GitLab CI/CD (5 stages) |
| Live Deployment | Proxmox VE 8.4.14, Ubuntu 22.04 VM |
| Deployment Prep | Kubernetes YAML manifests (10 files) |
| IaC | Terraform (5 files) |
| Operations | Backup script, monitoring plan |

---

## Quick Start (Local)

### Prerequisites
- Docker and Docker Compose installed
- Git

### Steps

```bash
# 1. Clone the repository
git clone https://gitlab.com/MunirAltawil/Doctor-Clinic-DevOps-System.git
cd Doctor-Clinic-DevOps-System

# 2. Copy environment file
cp .env.example .env

# 3. Configure database in .env
DB_HOST=mysql
DB_DATABASE=doktors
DB_USERNAME=doktors_user
DB_PASSWORD=doktors_pass

# 4. Build and start containers
docker compose up -d --build

# 5. Install PHP dependencies
docker compose exec app composer install

# 6. Generate application key
docker compose exec app php artisan key:generate

# 7. Run migrations and seeders
docker compose exec app php artisan migrate --force
docker compose exec app php artisan db:seed --force

# 8. Build frontend assets
docker compose exec app npm install
docker compose exec app npm run build

# 9. Fix storage permissions
docker compose exec app chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache
```

Application is available at: **http://localhost:8080**

---

## Repository Structure

```
app/                    Laravel application code
bootstrap/              Laravel bootstrap files
config/                 Application configuration
database/
  migrations/           16 database migrations
  seeders/              9 database seeders
docker/
  nginx/                Nginx configuration
k8s/                    10 Kubernetes YAML manifests
public/                 Public web root
resources/              Views, CSS, JS sources
routes/                 Laravel route definitions
scripts/                Backup automation scripts
terraform/              IaC starter files (5 files)
tests/                  PHPUnit test suite
.gitlab-ci.yml          GitLab CI/CD pipeline (5 stages)
docker-compose.yml      Docker Compose stack definition
Dockerfile              PHP 8.2-FPM application image
monitoring-plan.md      Monitoring strategy documentation
```

---

## CI/CD Pipeline (GitLab)

The pipeline runs automatically on every push:

| Stage | Job | Description |
|-------|-----|-------------|
| validate | php_syntax | PHP lint check on all source files |
| build | build_frontend | npm ci + npm run build (Vite) |
| test | test_application | SQLite DB + migrations + PHPUnit tests |
| package | package_project | tar.gz release archive |
| deploy | deploy_placeholder | Deployment to target environment |

---

## Live Deployment (Proxmox)

The application is deployed on Proxmox VE 8.4.14:

| Property | Value |
|----------|-------|
| Public URL | http://51.158.200.127:8080 |
| Proxmox Host | april26-bootcamp-dataops |
| VM | 100 / Doctors-Clinic-DevOps-System |
| OS | Ubuntu 22.04.5 LTS |
| VM Resources | 2 vCPU / 4 GB RAM / 22 GB Disk |
| Network | vmbr1 (10.10.10.100) + iptables NAT |

To verify the live deployment:
```bash
docker compose ps
# Expected: doktors_app, doktors_mysql, doktors_nginx all Up
```

---

## Kubernetes (Future Deployment)

Manifests in `k8s/`:
- `namespace.yaml` – dedicated namespace
- `secrets.yaml` – encoded credentials
- `pvc.yaml` – persistent volume
- `mysql-deployment.yaml` + `mysql-service.yaml`
- `app-deployment.yaml` + `app-service.yaml`
- `nginx-configmap.yaml` + `nginx-deployment.yaml` + `nginx-service.yaml`

```bash
kubectl apply -f k8s/
```

---

## Infrastructure as Code (Terraform)

Files in `terraform/`:
```bash
cp terraform/terraform.tfvars.example terraform/terraform.tfvars
# Edit terraform.tfvars with your values
terraform init
terraform plan
terraform apply
```

---

## Backup

```bash
# Run backup script
./scripts/backup.ps1
# Creates: MySQL dump + public/storage archive
```

---

## Documentation

| Document | Description |
|----------|-------------|
| 01_Project_Specifications | Business need, objectives, technology stack |
| 02_Architecture_and_Diagrams | System architecture, network diagram, CI/CD flow |
| 03_Requirements_Mapping | Institute requirements coverage matrix |
| 04_Delivery_Checklist | Final submission evidence checklist |
| 05_Executive_Report | Full project report with challenges and results |
| 06_Proxmox_Deployment_Evidence | Live deployment proof with commands and outputs |

---

## Author

**Muhammed Munir Al Tawil**  
DevOps – Application Deployment and Lifecycle  
DataScientest – Sorbonne University Partnership – 2026  
Mentor: Durrell Liora
