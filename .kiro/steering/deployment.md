---
inclusion: auto
---

# Deployment Standards

- No localhost — everything runs on cloud VM in production.
- Docker for containerization.
- Nginx as reverse proxy.
- Ports: 80/443 (Nginx), 3000 (frontend), 8080 (backend), 5432 (PostgreSQL).
- SSL via Certbot / Let's Encrypt.
- Environment variables for all credentials — never hardcode.
- Deploy flow: push to GitHub → pull on VM → build → restart containers.
