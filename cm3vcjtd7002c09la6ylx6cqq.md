---
title: "🚀 2nd week of my DevOps Journey: Multi-VM Setup and Hosting with Vagrant"
datePublished: Sun Nov 24 2024 08:38:08 GMT+0000 (Coordinated Universal Time)
cuid: cm3vcjtd7002c09la6ylx6cqq
slug: 2nd-week-of-my-devops-journey-multi-vm-setup-and-hosting-with-vagrant
tags: vagrant, automation, devops, iac, multiple-vm

---

Welcome back, everyone! In my ongoing **DevOps Journey**, I took a major step forward this week in building a **multi-node infrastructure** using **Vagrant**. This week was all about automating VM provisioning, hosting dynamic web applications, and applying my growing skills in **Infrastructure as Code (IaC)**.

Let me walk you through the exciting progress I made!

---

### 🛠️ **This Week's Achievements**

I took on the challenge of creating a **multi-VM setup** that mimics real-world server environments. Here's what I accomplished:

#### 1️⃣ **Multi-VM Setup with Vagrant**

I configured two virtual machines:

* **Node 1: Ubuntu with WordPress Hosting**
    
    * Set up **WordPress** on an **Ubuntu VM** using a LAMP stack (Linux, Apache, MySQL, PHP).
        
    * Automated the entire process with shell provisioning scripts.
        
* **Node 2: CentOS Stream 9 with Static Website**
    
    * Deployed a **static website** using the **Moso Interior template** on a **CentOS Stream 9 VM**.
        
    * Configured **Apache** to serve the website.
        

#### 2️⃣ **Private Networking for Seamless Communication**

Both VMs were set up with **private networking**, ensuring secure and isolated communication:

* **Ubuntu Node (WordPress)**: `192.168.56.10`
    
* **CentOS Node (Static Website)**: `192.168.56.11`
    

This configuration allows for smooth interaction between the two nodes, perfect for testing and development.

#### 3️⃣ **Automating Provisioning**

To automate the setup, I created and used the following shell scripts:

* **Ubuntu Provisioning Script**:
    
    * Installs Apache, MySQL, PHP, and sets up a WordPress site.
        
    * Configures MySQL and WordPress with the appropriate settings.
        
* **CentOS Provisioning Script**:
    
    * Installs Apache, downloads the static website template, and sets up the site on `/var/www/html/`.
        
    * Disables the firewall (be cautious when applying this in production).
        

Both provisioning scripts are executed automatically when the VMs are brought up using `vagrant up`.

#### 4️⃣ **Streamlined Management with Vagrantfile**

I used a **single Vagrantfile** to define and manage both VMs, ensuring that I can easily bring up, configure, and destroy the environment with a few simple commands.

---

### 🔍 **Key Takeaways**

* **Automation & IaC**: By using **Vagrant**, I automated the deployment and configuration of virtual machines, cutting down manual effort and ensuring consistency across environments.
    
* **Real-World Applications**: I successfully hosted a **WordPress site** on Ubuntu and a **static website** on CentOS, demonstrating the practical value of multi-VM environments.
    
* **Network Configuration**: I gained hands-on experience in managing **private networks**, an essential part of DevOps for maintaining secure communication between VMs.
    

---

### ⚙️ **How You Can Try It Too**

If you're eager to try this out, I've made the full setup available on my **GitHub repository**:  
👉 [IAC\_Infrastructure\_as\_Code](https://github.com/Yashraj-Garnayak/DevOps_Jorney/tree/main/IAC_Infrastructure_as_Code)

Here's how to get started:

1. Clone the repository to your local machine.
    
2. Ensure you have **Vagrant** and a compatible **VMware provider** installed.
    
3. Run the following command to start your VMs:
    
    ```bash
    vagrant up
    ```
    
4. Access the deployed applications:
    
    * WordPress (Ubuntu): [http://192.168.56.10](http://192.168.56.10)
        
    * Static Website (CentOS): http://192.168.56.11
        

---

### 📝 **Inside the Scripts**

#### **Ubuntu Provisioning Script (**`ubuntu_script.sh`)

This script installs everything needed for **WordPress**: Apache, MySQL, PHP, and the WordPress site itself. It creates the database, sets user permissions, and configures WordPress' `wp-config.php` file for database access.

```bash
bashCopy code#!/bin/bash
sudo apt update
sudo apt install apache2 ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip -y
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
...
```

#### **CentOS Provisioning Script (**`centos_script.sh`)

This script installs Apache, downloads a **static website template**, and sets it up on the CentOS server. It then restarts Apache to serve the new site.

```bash
bashCopy code#!/bin/bash
yum update -y
yum install httpd wget unzip -y
systemctl start httpd
systemctl enable httpd
systemctl stop firewalld
mkdir -p /tmp/website
cd /tmp/website
wget https://www.tooplate.com/zip-templates/2133_moso_interior.zip
unzip -o 2133_moso_interior.zip
cp -r 2133_moso_interior/* /var/www/html/
...
```

---

### 📈 **Why This Matters**

By setting up multi-node environments and automating provisioning, I’m learning how to simulate real-world scenarios where multiple VMs are required. This skill is essential for DevOps, as it allows for rapid deployment, testing, and scaling of applications.

---

### 🔮 **Next Steps**

I’m now looking forward to:

* Experimenting with **advanced provisioning tools** like Ansible to automate even more complex setups.
    
* Expanding my **CI/CD workflows** and integrating these environments into the deployment pipeline.
    
* Exploring **cloud-based infrastructure** to scale these concepts beyond local VMs.
    

---

That’s it for this week’s update in my DevOps journey! I hope you found this post helpful. If you have any questions or feedback, feel free to drop them in the comments. Let's keep pushing forward!

#DevOps #IAC #Vagrant #Ubuntu #CentOS #Automation #WordPress #StaticWebsite #MultiVM #IaC