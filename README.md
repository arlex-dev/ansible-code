# ⚙️ Ansible — AWS EC2 Server Configuration

**Arlex | Cloud & DevOps Engineer | github.com/arlex-dev**

---

## 📋 Overview
Ansible playbooks to automate configuration management on 
AWS EC2 instances. Targets two environments — dev and QA 
servers — and automates user creation, directory setup, 
and package installation.

---

## 🏗️ Architecture

~~~
Ansible Controller (local)
         ↓ SSH (keypair.pem)
    ┌────────────┐
    │            │
devserver      qaserver
(EC2)          (EC2)
    │            │
play.yml      web.yml
~~~

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Ansible | Configuration management & automation |
| AWS EC2 | Target servers (dev + QA) |
| YAML | Playbook & inventory language |
| SSH | Secure connection to EC2 instances |

---

## 📁 Project Structure

~~~
ansible-code/
│
├── ansible.cfg     # Ansible config (SSH, logging, inventory path)
├── inv.yml         # Inventory — dev and QA EC2 servers
├── play.yml        # Dev server playbook
└── web.yml         # QA server playbook
~~~

---

## ⚙️ What the Playbooks Do

### play.yml — Dev Server
- Creates a Linux user (arlex)
- Creates files and directories
- Installs Apache (httpd)
- Installs wget, samba, java-8, finger

### web.yml — QA Server
- Installs unzip, wget, httpd

---

## 🚀 How to Run

~~~bash
# Test connectivity to all servers
ansible all -i inv.yml -m ping

# Run dev server playbook
ansible-playbook -i inv.yml play.yml

# Run QA server playbook
ansible-playbook -i inv.yml web.yml
~~~

---

## 🔑 Key Concepts

- Inventory file separates dev and QA environments
- Playbooks use variables for reusable package names
- Ansible connects via SSH — no agent needed on target servers
- host_key_checking disabled for EC2 dynamic IPs

---

## 👤 Author
Arlex — github.com/arlex-dev
