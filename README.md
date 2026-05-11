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
