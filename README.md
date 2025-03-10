# Enterprise Ansible Automation Playbooks

## Overview

This repository contains a comprehensive collection of Ansible playbooks designed for enterprise-grade infrastructure automation and configuration management. These playbooks implement infrastructure as code principles to provide consistent, repeatable, and auditable infrastructure configurations across development, staging, and production environments.

## Repository Structure

```
ansible-playbooks/
├── inventory/                     # Host inventory files
│   ├── development/
│   ├── staging/
│   └── production/
├── group_vars/                    # Group variables
│   ├── all/
│   ├── webservers/
│   └── databases/
├── host_vars/                     # Host-specific variables
├── roles/                         # Reusable Ansible roles
│   ├── common/                    # Base configuration for all servers
│   ├── webserver/                 # Web server configuration (NGINX, Apache)
│   ├── database/                  # Database server configuration (MySQL, PostgreSQL)
│   ├── monitoring/                # Monitoring agent installation and configuration
│   ├── security/                  # Security hardening and compliance
│   └── backup/                    # Backup configuration
├── playbooks/                     # Task-specific playbooks
│   ├── site.yml                   # Main playbook that includes all others
│   ├── webserver.yml              # Web server specific tasks
│   ├── database.yml               # Database specific tasks
│   ├── security.yml               # Security hardening tasks
│   └── maintenance.yml            # Maintenance tasks
└── scripts/                       # Helper scripts and utilities
```

## Key Features

- **Environment Segregation**: Separate inventory and configuration for development, staging, and production environments
- **Role-Based Organization**: Modular roles that can be composed into comprehensive server configurations
- **Security Compliance**: Integrated security hardening based on industry best practices
- **Idempotent Execution**: Safe to run multiple times without causing unintended side effects
- **Comprehensive Documentation**: Well-documented roles and playbooks for ease of use
- **CI/CD Integration**: Designed to work with popular CI/CD pipelines
- **Parameterized Deployments**: Flexible configuration using variables

## Prerequisites

- Ansible 2.9 or newer
- SSH access to target servers
- Appropriate sudo privileges on target servers
- Python 2.7+ or 3.6+ on target servers

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Alexander77063/ansible-playbooks.git
   cd ansible-playbooks
   ```

2. **Update inventory files with your server information:**
   ```bash
   vi inventory/development/hosts
   ```

3. **Review and customize variables:**
   ```bash
   vi group_vars/all/main.yml
   ```

4. **Run the main playbook:**
   ```bash
   ansible-playbook -i inventory/development/hosts playbooks/site.yml
   ```

5. **Run specific role playbooks as needed:**
   ```bash
   ansible-playbook -i inventory/development/hosts playbooks/webserver.yml
   ```

## Featured Playbooks

### Web Server Configuration

Automates the installation and configuration of web servers with the following capabilities:

- NGINX or Apache installation and optimization
- Virtual host configuration
- SSL/TLS certificate management
- PHP-FPM setup and optimization
- Static content deployment
- Load balancer integration

### Database Server Configuration

Provides comprehensive database server setup including:

- MySQL/PostgreSQL installation and hardening
- Database creation and user management
- Backup configuration
- Performance tuning
- Replication setup
- Monitoring integration

### Security Hardening

Implements security best practices across all servers:

- Firewall configuration
- SSH hardening
- User access control
- File system permissions
- Security updates
- Compliance scanning

## Usage Examples

### Complete Environment Setup

```bash
ansible-playbook -i inventory/production/hosts playbooks/site.yml
```

### Web Server Deployment

```bash
ansible-playbook -i inventory/staging/hosts playbooks/webserver.yml -e "app_version=1.2.3"
```

### Security Update

```bash
ansible-playbook -i inventory/production/hosts playbooks/security.yml --tags "updates"
```

## Best Practices

This repository follows Ansible best practices, including:

- Version-controlled infrastructure
- Separation of code and configuration
- Task tagging for selective execution
- Encrypted sensitive data using Ansible Vault
- Pre and post deployment validation
- Comprehensive error handling
