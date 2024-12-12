---
title: "🚀 How to Launch an EC2 Instance in the New AWS Console"
seoTitle: "How to launch an ec2 instance with new aws console"
seoDescription: "Learn how to launch an EC2 instance in AWS Console effortlessly with this step-by-step guide for deploying, hosting, and scaling resources"
datePublished: Wed Dec 11 2024 03:12:18 GMT+0000 (Coordinated Universal Time)
cuid: cm4jbe9rx000008mh89r8brtw
slug: how-to-launch-an-ec2-instance-in-the-new-aws-console
tags: ec2, linux, aws, cloud-computing, virtual-machines, aws-console, securitygroups, cloud-infrastructure, ec2-instance, tech-tutorial, techblogs, launchec2, awsconfiguration, awsforbeginners, awsinstancesetup

---

Launching an EC2 instance is the first step towards harnessing the power of cloud computing in AWS! Whether you're deploying a web server, hosting an application, or experimenting with different technologies, AWS EC2 (Elastic Compute Cloud) gives you the flexibility to scale your resources on demand. Here's a step-by-step and easy-to-follow guide to launching your EC2 instance on the latest AWS Console. 🌟

---

# Step 1: 🔐 **Log into Your AWS Console**

* Open the AWS Console in your browser and log in with your AWS credentials.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733884585532/022b1924-9dc8-466c-b603-d7efe855f32a.png align="center")
    

# Step 2: 🔍 **Search for EC2**

* In the search bar at the top, type **EC2** and select **EC2 Dashboard**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733884629333/aed2f89e-d791-417e-bf66-337653b0223f.png align="center")
    

# Step 3: 🖥️ **Access the Instances Section**

* On the left side, click on **Instances** to go to the **Instances Dashboard**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733884653471/9fcb734b-c302-49b8-9d45-42bb1e260ee6.png align="center")
    

# Step 4: ⚡ **Launch an Instance**

* In the Instances Dashboard, look at the top right corner for the **Launch Instance** button. Click it to open the new page where you can configure your instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733884694779/fd2a2678-4051-4e6c-9ee3-4625477a2c7f.png align="center")
    

# Step 5: 🛠️ **Configure Your Instance**

## Step 5.1: 🏷️ **Name Your Instance**

* Give your instance a name, such as **demo** (or any name you prefer).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733884972915/c91c29d8-f737-4ccc-828b-7fbe702bad0e.png align="center")
    

## Step 5.2: 🖥️ **Select an Image for Your Instance**

* Choose an **Amazon Machine Image (AMI)**, which determines the operating system for your instance.
    

## Step 5.3: 🛸 **Choose an Instance Type**

* Select an instance type. I’ll choose **t2.micro**, which is eligible for the AWS free tier (1 vCPU and 1 GB of RAM).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885083116/6562739f-c467-43cc-a381-d71972b6f1c1.png align="center")
    

## Step 5.4: 🔑 **Key Pair Login**

* Select a **key pair**. A key pair allows you to SSH into your AWS instance from your local machine.
    
    * If you don’t have one, create a new key pair.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885128474/6cf0811e-6933-40a3-b99d-24066a167f1f.png align="center")
        

### Step 5.4.1: 🏷️ **Name Your Key Pair**

* Name your key pair, e.g., **demo-keypair**. Choose **.pem** format if you’re using macOS, or **.ppk** if on Windows with PuTTY.
    
* Click **Create**, and AWS will generate a key pair and automatically download the **.pem** file.
    
* Select your key pair from the list.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885199813/1de62e15-e625-4484-8ca9-fd2132bcbe29.png align="center")
    

## Step 5.5: 🌐 **Configure Network Settings**

### Step 5.5.1: 🏠 **VPC Configuration**

* For now, leave everything as default, including the VPC.
    

### Step 5.5.2: 🔒 **Configure Firewall Settings**

* You can either leave the default firewall settings with SSH access or create a **security group** with custom inbound and outbound rules.
    
    * To skip custom rules, just select SSH and HTTP access.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885388128/23140ae8-ef7b-4098-80f9-32f8eb00328a.png align="center")
        

###### Step 5.5.2.1: 🔐 **Create a Security Group**

* **What is a security group?**
    
    * A **security group** acts as a virtual firewall for your instance to control inbound and outbound traffic. It is used to define which IP addresses can communicate with your EC2 instance over specific ports like HTTP, SSH, etc.
        
    
    1. Go to **Security Groups** in the EC2 Dashboard and create a new one, e.g., **demo-test**.
        
    2. **Inbound Rules**:
        
        * **Rule 1:** I want to access my instance via **SSH**, so I’ll provide inbound SSH access from everyone. Select the type as **SSH**, and for source, select **0.0.0.0/0** (anyone can access via SSH).
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885473274/cf16c29a-e6d2-4d5e-9a12-e7c4391bc006.png align="center")
            
        * Rule 2: **Rule 2:** I want to access the instance from the internet. To configure this as a server, select the type as **HTTP** and the source as **0.0.0.0/0** (anyone can access via HTTP).
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885500978/3f7c6b54-40bd-49b7-902c-8f3c3aea5af5.png align="center")
            
    3. **Outbound Rules**:
        
        * **Rule 1:** I want to give the instance internet access because we will update the instance and download **httpd** for hosting the server. Select the type as **All Traffic** and the source as **0.0.0.0/0** (anyone can access anything on the internet).
            
    4. **Now create the security group**: After you create the security group, go back to the EC2 instance launch page.
        
    5. **Select the Existing Security Group**:
        
        * Click on **Select Existing Security Groups**.
            
        * Choose the **demo-test** security group you just created.
            
        * If it doesn't show up immediately, click the **refresh** button next to the list of security groups. Don’t refresh the entire page; just click the circle next to the security group list.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885820757/c30ff0e4-3d89-4e11-b84a-2a7295cc0fb4.png align="center")
            

# Step 5.6: 💾 **Configure Storage**

* Leave the storage settings as default. It will create an **EBS volume** and attach it to your instance.
    
    * If you want more storage, you can increase it, but I recommend staying within the free tier (30 GB for total EBS volume).
        

## Step 5.7: 📝 **Configure User Data**

* **What is user data?**
    
    * User data is a script that runs when the instance starts, and it helps automate the setup.
        
    * Click on **Advanced Settings**, go to **User Data**, and paste the following script:
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733885895360/14ec981e-6ced-453e-a725-11429a1afb7b.png align="center")
    
    * Script:
        
    
    ```bash
    #!/bin/bash
    sudo yum -y update
    sudo yum -y install httpd
    sudo systemctl start httpd
    sudo systemctl enable httpd
    echo "<h1>My instance is running</h1>" | sudo tee /var/www/html/index.html
    sudo systemctl restart httpd
    ```
    

### Step 6: ⏳ **Wait for the Instance to Initialize**

* Go to the **Instances Dashboard** and wait for the instance to reach the **running** state.
    
* You’ll see the instance initializing.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733886241315/5a5765c7-628c-4d2c-8ae1-f7e023222a3a.png align="center")
    

#### Step 7: 🌍 **Check the Instance’s Public IP**

* Click on the instance, and in the lower section, find the **Public IP**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733886262858/227941d7-6e55-407c-89ad-f82348a176bb.png align="center")
    
* Copy the **Public IP** and paste it into your browser:
    
    ```bash
    http://<public_ip_address>
    ```
    
* Voila! 🎉 You’ll see a page displaying: **“My instance is running”**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733886286673/f71b2561-fbf1-498e-a961-156c54cc62fd.png align="center")
    

---

### Conclusion 🌟

Congratulations! You've successfully launched an EC2 instance in AWS. 🎉 Now you can use your instance for development, testing, or even as a public web server. The AWS cloud offers incredible flexibility, so feel free to explore more options, adjust configurations, and scale as your needs grow.