# Deployment Guide Outline: GitHub → Ubuntu Server (VM)

---

#### **1. Server Installation & Preparation**

- 1.1 Choose a virtualization environment (e.g., Proxmox, VirtualBox, VMware, or cloud providers like AWS/DO/Vultr)
- 1.2 Install Ubuntu Server (LTS version recommended)
- 1.3 Configure static IP or ensure proper DNS resolution
- 1.4 Create a non-root `devops` or `deploy` user with `sudo` privileges
- 1.5 Harden SSH (disable root login, use public-key auth)

---

#### **2. Initial Server Setup**

- 2.1 Update and upgrade packages
- 2.2 Set timezone and locale
- 2.3 Install essential tools (git, curl, unzip, build-essential, ufw)
- 2.4 Configure firewall rules (UFW or iptables)

---

#### **3. SSH Key-Based GitHub Access**

- 3.1 Generate SSH key on VM
- 3.2 Add public key to GitHub Deploy Keys or your user account
- 3.3 Test `git clone` from private repo

---

#### **4. Setup Deployment Environment**

- 4.1 Install Node.js / Python / Java / Docker depending on the project
- 4.2 Install a process manager (e.g., PM2, systemd, or Docker Compose)
- 4.3 Setup a reverse proxy (e.g., Nginx or Caddy) with optional TLS via Let’s Encrypt

---

#### **5. CI/CD Pipeline Setup**

- 5.1 Configure GitHub Actions

  - 5.1.1 Set up workflow file with SSH deploy job
  - 5.1.2 Store private SSH key and host fingerprint as GitHub secrets

- 5.2 Write the deploy script on VM (pull repo, install dependencies, restart service)
- 5.3 Test manual and automatic deploys

---

#### **6. File Upload Handling (Local Storage)**

- 6.1 Create a directory with write permissions for uploads
- 6.2 Handle path resolution securely in your backend
- 6.3 Configure Nginx or reverse proxy to serve static files from that directory

---

#### **7. Monitoring & Maintenance**

- 7.1 Install monitoring tools (e.g., `htop`, `netdata`, `fail2ban`)
- 7.2 Setup basic logging and log rotation
- 7.3 Schedule backups (cron jobs or rsync-based)

---

Let me know if you'd like me to expand any of these sections, or if your setup includes special considerations like Docker, HTTPS, or multi-node deployment. You can also request [server hardening tips](f), [CI/CD examples](f), or [reverse proxy setup](f).
