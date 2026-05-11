# Doctor Clinic DevOps System

A Laravel-based clinic appointment platform enhanced with DevOps practices including Docker, CI/CD, Kubernetes manifests, backup automation, monitoring documentation, and Terraform IaC structure.

---

## Project Overview

The system provides a complete clinic workflow for:

- **Patients** to browse doctors and book appointments
- **Doctors** to manage availability and appointments
- **Admins** to manage users, specialties, settings, pages, and reports

This repository represents the **DevOps-oriented version** of the Doctor Clinic System project.

---

## Core Application Features

### Patient
- Register and log in
- Browse specialties and doctors
- Book appointments
- View appointments

### Doctor
- Register and wait for admin approval
- Manage profile
- Define working hours and availability
- Track appointments and reports

### Admin
- Approve or reject doctors
- Manage users
- Manage specialties
- Manage public pages
- Monitor appointments and reports

---

## Tech Stack

### Application
- **Backend:** Laravel / PHP
- **Frontend:** Blade, Tailwind CSS, Alpine.js
- **Database:** MySQL
- **Assets:** Vite
- **Authentication:** Laravel Breeze

### DevOps
- **Containerization:** Docker, Docker Compose
- **CI/CD:** GitHub Actions
- **Orchestration:** Kubernetes manifests
- **Backup:** PowerShell backup script
- **Monitoring:** Documented monitoring plan
- **IaC:** Terraform starter structure

---

## DevOps Enhancements Implemented

This project was extended with the following DevOps deliverables:

- Dockerized Laravel application
- Docker Compose setup for:
  - app
  - nginx
  - mysql
- Automated test execution through GitHub Actions
- Frontend asset build in CI
- Initial Kubernetes manifests
- Backup automation script
- Monitoring plan documentation
- Terraform Infrastructure-as-Code starter layer

---

## Repository Structure

```bash
app/
bootstrap/
config/
database/
docker/
k8s/
public/
resources/
routes/
scripts/
storage/
terraform/
tests/
.github/workflows/
DEVOPS-IMPLEMENTATION.md
monitoring-plan.md
Dockerfile
docker-compose.yml
README.md
Running the Project with Docker
1. Build and start containers
docker compose up -d --build
2. Generate application key
docker compose exec app php artisan key:generate
3. Run migrations
docker compose exec app php artisan migrate
4. Seed demo data
docker compose exec app php artisan db:seed
5. Create storage link
docker compose exec app php artisan storage:link
6. Open the application

http://localhost:8080

Running Tests
Run all tests
docker compose exec app php artisan test
Current status

All project tests are passing in the Docker environment.

CI/CD

GitHub Actions workflow is configured in:

.github/workflows/ci.yml

The pipeline performs the following steps:

checkout code
set up PHP
set up Node.js
install Composer dependencies
install NPM dependencies
build Vite assets
generate app key
configure test database
run migrations
clear caches
run automated tests
Kubernetes

Initial Kubernetes manifests are available in:

k8s/

Included resources:

Namespace
Secret
PersistentVolumeClaim
MySQL Deployment
MySQL Service
App Deployment
App Service
Nginx ConfigMap
Nginx Deployment
Nginx Service
Important Note

These manifests are an initial deployment draft and may require further improvement for full production use, especially regarding:

real image registry usage
application secret management
APP_KEY replacement
shared storage strategy
ingress / probes / scaling
Backup

Backup automation is available in:

scripts/backup.ps1

This script creates:

a MySQL database dump
an archive of public storage files
Run backup
powershell -ExecutionPolicy Bypass -File .\scripts\backup.ps1
Monitoring

Monitoring documentation is available in:

monitoring-plan.md

The monitoring plan covers:

application health checks
nginx availability
mysql availability
logs
uptime
response time
future Prometheus/Grafana integration
Terraform / IaC

Terraform starter files are available in:

terraform/

Included files:

provider.tf
variables.tf
main.tf
outputs.tf
terraform.tfvars.example
README.md

This layer is intended as an initial Infrastructure-as-Code structure for future extension.

Additional Documentation
DEVOPS-IMPLEMENTATION.md -> project DevOps summary
monitoring-plan.md -> monitoring strategy
terraform/README.md -> Terraform explanation
Current DevOps Status

Implemented:

Docker
Docker Compose
CI pipeline
automated testing
Kubernetes starter manifests
backup script
monitoring documentation
Terraform starter structure

Remaining future improvements:

container image registry publishing
stronger Kubernetes deployment design
real secret management
production monitoring stack
GitLab CI/CD if required
Proxmox-oriented IaC extension

Author
Muhammed Munir Al Tawil
