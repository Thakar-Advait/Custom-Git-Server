
# 🌐 Personal Git Server Infrastructure: A Deep Dive into Version Control

## 📘 Project Overview

This project provides a comprehensive guide to setting up a personal Git server, offering deep insights into version control mechanisms and repository management. By following these steps, you'll create a very minimalist GitHub-like infrastructure that gives you control over your code repositories.

### 🎯 Project Mission

**Why Build Your Own Git Server?**

-   💡 Gain unprecedented insights into version control systems
-   🔒 Enhance your understanding of repository management
-   🛠️ Learn advanced DevOps and server configuration techniques
-   🌈 Create a fully customizable, secure Git hosting solution

## 🌟 Key Features

1.  Setup your own git server on a virtual machine
2.  Visualize the inner workings of git using a simple WebUI
3.  Connect your VM to a domain to replicate GitHub-like website
4.  Implement SSL certification for secure access

## 🛠 Technology Stack

-   **Version Control**: Git
-   **Web Interface**: GitWeb
-   **Cloud Platform**: Google Cloud
-   **Authentication**: SSH
-   **Web Server**: Nginx
-   **SSL Certification**: Certbot

## 🖼 Project Visualizations

### Git WebUI: Repository History

![Git WebUI Repository History](https://res.cloudinary.com/dpdyyyxut/image/upload/v1743154815/Screenshot_2025-03-27_at_6.00.12_PM_antnvc.png)

### Git WebUI: Commit Differences

![Git WebUI Commit Differences](https://res.cloudinary.com/dpdyyyxut/image/upload/v1743154816/Screenshot_2025-03-27_at_6.00.18_PM_iyxo4u.png)

### Virtual Machine Terminal

![Virtual Machine Terminal](https://res.cloudinary.com/dpdyyyxut/image/upload/v1743154831/Screenshot_2025-03-27_at_6.01.49_PM_vvhis0.png)

## 🚀 Comprehensive Installation Guide

### 1. Virtual Machine Preparation

**Purpose:** Create an isolated, controlled environment for your Git server

1.  Create a Virtual Machine on Google Cloud with an Ubuntu OS image
    
    -   Allow HTTP and HTTPS traffic in the VM firewall
    -   Choose a region close to your primary users for better latency
2.  Update and upgrade system packages:
    
    ```bash
    sudo apt update
    sudo apt upgrade
    
    ```
    

**Why This Step Matters:**

-   Ensures you have the latest security patches
-   Prepares a clean, up-to-date environment for your Git server
-   Reduces potential vulnerabilities

### 2. User and Permission Setup

1.  Set root user password:
    
    ```bash
    sudo passwd root
    
    ```
    
2.  Create a dedicated Git user:
    
    ```bash
    sudo adduser git
    
    ```
    
3.  Grant necessary permissions:
    
    ```bash
    sudo usermod -aG sudo git
    
    ```
    

**Key Considerations:**

-   Isolate Git operations to a dedicated user
-   Implement principle of least privilege
-   Enhance system security by restricting access

### 3. SSH Authentication

1.  Generate SSH key on local machine:
    
    ```bash
    ssh-keygen -t ed25519 -C "your_email@example.com"
    
    ```
    
2.  Copy public key to VM:
    
    ```bash
    # On local machine
    cat ~/.ssh/id_ed25519.pub
    
    # On VM, add the key to ~/.ssh/authorized_keys
    
    ```
    

**Why Public Key Authentication?**

-   More secure than password-based login
-   Cryptographically robust
-   Supports key-based access across multiple devices

### 4. Git Repository Setup

1.  Create a new repository:
    
    ```bash
    sudo mkdir -p /var/lib/git/new-project.git
    cd /var/lib/git/new-project.git
    sudo git init --bare
    sudo chown -R git:git /var/lib/git
    
    ```
    
2.  Clone the repository to local machine:
    
    ```bash
    git clone git@<your_vm_public_ip>:/var/lib/git/new-project.git
    
    ```
    

### 5. GitWeb Installation

1.  Install required packages:
    
    ```bash
    sudo apt install ruby git-core gitweb
    
    ```
    
2.  Start GitWeb:
    
    ```bash
    git instaweb --httpd=webrick
    
    ```
    
3.  Access WebUI:
    
    -   Navigate to `http://<your_VM_public_ip>:1234`

### 6. Nginx and SSL Configuration

#### Nginx Installation

Refer to detailed guides:

-   [Nginx Installation](https://docs.chaicode.com/nginx-install/)
-   [Nginx Configuration on Ubuntu](https://docs.chaicode.com/nginx-config/)

#### SSL Certificate

Follow the guide for [SSL Setup in Nginx Ubuntu](https://docs.chaicode.com/ssl-in-nginx-ubuntu/)

### 7. Workflow Examples

#### Pushing Changes

```bash
git checkout -b master
git add .
git commit -m "Committing to git server"
git push -u origin master

```

## 🔒 Security Best Practices

-   Use strong, unique SSH keys
-   Regularly update system packages
-   Configure firewall rules
-   Implement fail2ban for additional protection

## 🤝 Contributing

Contributions are welcome! Some ways you can help:

-   Improve documentation
-   Enhance security configurations
-   Add more robust authentication methods
-   Create scripts for easier setup

### Contribution Steps

1.  Fork the repository
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 📞 Contact

Advait Thakar - [contact@advait-thakar.work](mailto:contact@advait-thakar.work)

----------

** 
This project demonstrates not just technical skills, but a deep understanding of infrastructure, security, and version control principles. It's a testament to comprehensive, professional-grade software engineering practices.
**
