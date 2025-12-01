
---

# Automated Nginx Deployment with Ansible

## Project Title
**Automated Deployment with Ansible and Nginx**

## Project Overview
This DevOps project demonstrates a fully automated, idempotent deployment of a simple static website across multiple web servers using Ansible. The website is served by Nginx and displays:

• A success message confirming deployment via Ansible  
• Team member names  
• The hostname of the server (injected with Ansible facts)

## Project Structure

. ├── ansible.cfg                # optional Ansible configuration ├── inventory.ini              # Inventory file with target servers ├── playbook.yml               # Main Ansible playbook ├── templates/ │   └── index.html.j2          # Jinja2 template for the webpage └── README.md                  # This file

## Inventory (inventory.ini)
All servers are Ubuntu based and reachable through SSH using the **ubuntu** user with key based authentication.

## Ansible Playbook (playbook.yml)
The automation script installs Nginx, creates required folders, and deploys the webpage on all servers.

## Webpage Template (templates/index.html.j2)
The webpage content is a Jinja2 template so Ansible can dynamically insert the hostname (`{{ inventory_hostname }}`) into the page. Each server shows its own name.

## How to Run the Project

### 1. Prerequisites
• Control node with Ansible installed (version 2.9 or newer)  
• SSH key access to target servers as the **ubuntu** user

### 2. Run the playbook
```bash
ansible-playbook playbook.yml

3. Verify Deployment

Visit any of the server IPs in a browser:

• http://10.240.184.138
• http://10.240.184.121
• http://10.240.184.37

You should see the custom page with the correct server hostname.

Benefits

• Fully automated and repeatable
• Idempotent which means safe to run multiple times
• Easy to scale by adding hosts to the inventory
• Clear separation of configuration and content

Future Enhancements

• Add HTTPS with Lets Encrypt
• CI or CD integration with GitHub Actions
• Convert to reusable Ansible roles
• Add load balancing or health checks
• Deploy a real application instead of static content

---