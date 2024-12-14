---
title: "Amazon Elastic Load Balancer: A Step-by-Step Guide ✨"
seoTitle: "How to Create an Amazon Elastic Load Balancer (ALB) | Step-by-Step Gui"
seoDescription: "Learn how to create an Amazon Elastic Load Balancer (ALB) step by step. This guide covers EC2 instances, target groups, and ALB setup with real-life example"
datePublished: Sat Dec 14 2024 07:26:31 GMT+0000 (Coordinated Universal Time)
cuid: cm4nusqsl001309kz627qc6t9
slug: amazon-elastic-load-balancer-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734161045828/05202bf4-0147-49a1-900a-467a03d7005c.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734161174059/f4673702-5f79-49b5-bcd6-222ee3c26d60.webp
tags: aws, web-development, cloud-computing, devops, scalability, amazonwebservices, high-availability, applicationloadbalancer, tech-guide, elasticloadbalancer

---

### Introduction to Elastic Load Balancer (ELB)

Amazon Elastic Load Balancer (ELB) is like a skilled traffic cop for your applications. 🚦 Imagine you run a busy restaurant with multiple chefs in different kitchens. To ensure every customer gets served efficiently, you need a manager who assigns tasks evenly to the chefs. Similarly, ELB distributes incoming traffic across multiple servers (or EC2 instances), ensuring your application remains highly available, fault-tolerant, and scalable.

---

### Types of Elastic Load Balancers 🛠️

Before diving into the steps, let’s explore the types of ELBs offered by AWS:

1. **Application Load Balancer (ALB)**:
    
    * Best for HTTP and HTTPS traffic.
        
    * Operates at the application layer (Layer 7).
        
    * Ideal for advanced routing, microservices, and serverless applications.
        
2. **Network Load Balancer (NLB)**:
    
    * Handles TCP, UDP, and TLS traffic.
        
    * Operates at the transport layer (Layer 4).
        
    * Designed for ultra-high performance.
        
3. **Gateway Load Balancer (GLB)**:
    
    * Simplifies the deployment, scaling, and management of third-party virtual appliances.
        
4. **Classic Load Balancer (CLB)** (Legacy):
    
    * Supports both Layer 4 and Layer 7.
        
    * Suitable for simple applications (not recommended for new designs).
        

For this tutorial, we’ll focus on creating an **Application Load Balancer (ALB)** to distribute traffic to multiple EC2 instances. 🚀

---

### Step-by-Step Guide to Create an Application Load Balancer

#### **Step 1: Log into Your AWS Console** 🔑

* Navigate to the EC2 service dashboard by searching "EC2" in the search bar.
    

#### **Step 2: Launch Multiple EC2 Instances**

* Create EC2 instances to serve as backend servers.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160134324/04413a16-495b-4942-bc5f-ce592a8e86c0.png align="center")
    
* Ensure instances are launched in different Availability Zones (AZs) for high availability:
    
    * **ap-south-1a**: 1 instance
        
    * **ap-south-1b**: 2 instances
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160166114/b1414cc7-2f40-4960-8d40-e9680b0ec4e7.png align="center")
        
* Verify that all instances are in the "running" state:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160291788/1ed3f2ff-c584-498a-973c-bae1f4a12a9d.png align="center")
    

#### **Step 3: Create a Target Group** 🎯

* **What is a Target Group?** It’s a logical grouping of EC2 instances that the ALB forwards traffic to.
    

1. Go to the "Target Groups" section under the Elastic Load Balancing category.
    
2. Click **Create Target Group**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160331137/99d73ad2-d376-405d-ad7c-bc813cbe6ee1.png align="center")
    
3. Name your Target Group (e.g., `alb-demo-tg`).
    
4. Choose the type as **Instances**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160400415/ec3f67e4-ef15-43f9-a16e-3c3e0a2ed36c.png align="center")
    
5. Select the instances you created earlier and include them as pending targets.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160665822/16de668f-98c0-4258-8a68-340c86473918.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160700506/f734413d-a8ff-40b4-996f-c30437e56121.png align="center")
    
6. Click **Create Target Group**. Walla! 🎉 You’ve created your Target Group.
    

#### **Step 4: Create an Application Load Balancer** 💻

1. Go to the "Load Balancers" section.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160740159/b664f580-90e5-4385-ba52-520138163ab1.png align="center")
    
2. Click **Create Load Balancer** and choose **Application Load Balancer**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160772876/3f4e3bb6-43ff-4b09-84ef-5b57794658f5.png align="center")
    
3. Configure the ALB:
    
    * **Name**: e.g., `alb-demo`.
        
    * **Scheme**: Choose "Internet-facing" for public traffic or "Internal" for private.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160810381/9d9904db-162b-4d8c-a9eb-9ea12d03052d.png align="center")
        
    * **Network Mapping**: Select the subnets for the Availability Zones where your instances are located (e.g., `ap-south-1a` and `ap-south-1b`).
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160863170/613ecc68-60a7-45c5-89be-5d0e46eb1ad8.png align="center")
        
    * **Security Group**: Assign a security group that allows HTTP/HTTPS traffic.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160878546/63ea788a-b8df-4e6a-91c8-4e893acad097.png align="center")
        

4. Attach the Target Group created in Step 3 to the ALB.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160907025/815be5fc-2196-451c-8ece-d1307d8585f6.png align="center")
    
5. Click **Create Load Balancer**. 🎉
    

#### **Step 5: Test Your ALB** 🌐

1. Copy the **DNS name** of the ALB (available in the Load Balancer details).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160956890/a840b678-59c4-4de0-b97c-5fae60c23b17.png align="center")
    
2. Paste it into your browser: `http://<dns_name>`.
    
3. If configured correctly, you’ll see the application hosted on your EC2 instances.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734160982365/51cb2ae0-7333-467f-b22b-bf7cb156adf5.png align="center")
    

---

### Real-Life Analogy for Better Understanding 🌟

Think of an Application Load Balancer as the receptionist at a hotel. Guests (traffic) arrive at the reception, and the receptionist directs them to the correct rooms (EC2 instances) based on availability and type of request. This ensures no room is overloaded, and every guest gets a smooth experience. 🏨

---

### Wrap-Up 🎁

Congratulations! You’ve successfully learned how to:

* Set up multiple EC2 instances.
    
* Create and configure a Target Group.
    
* Deploy an Application Load Balancer.
    
* Test its functionality.
    

Application Load Balancers are crucial for ensuring the scalability, availability, and resilience of modern applications. By understanding their setup and working, you’re one step closer to mastering AWS. 🌟

Got questions or feedback? Let us know in the comments below! 🚀