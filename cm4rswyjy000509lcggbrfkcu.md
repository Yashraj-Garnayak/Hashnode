---
title: "How to Create Path-Based Redirects for AWS Application Load Balancer 🌐"
seoTitle: "Path-Based Redirects in AWS Load Balancer"
seoDescription: "Learn how to create path-based redirects for AWS Application Load Balancer (ALB) with a complete step-by-step guide. Includes setting up EC2 instances, targ"
datePublished: Tue Dec 17 2024 01:44:53 GMT+0000 (Coordinated Universal Time)
cuid: cm4rswyjy000509lcggbrfkcu
slug: how-to-create-path-based-redirects-for-aws-application-load-balancer
tags: ec2, aws, cloud-computing, devops, alb, techblog, awsguide, elasticloadbalancer, pathbasedrouting, webtraffic

---

## What are Path-Based Redirects? 🤔

Path-based redirects allow you to route specific traffic to different servers or target groups based on the URL path. For example:

* Traffic to `/` (home page) can be sent to one group of servers.
    
* Traffic to `/test` (test page) can be sent to another group of servers.
    

This is particularly useful when managing multiple services or applications under a single load balancer. Let’s dive into the **step-by-step guide** to set up path-based redirects using AWS **Application Load Balancer (ALB)**.

---

## Steps to Create Path-Based Redirects for ALB 🚀

### Step 1: Log Into Your AWS Root Account 🔑

1. Log in to your AWS Management Console.
    
2. Change the **region** to `ap-south-1` (Mumbai).
    
3. Search for **EC2** in the search bar and go to the **EC2 dashboard**.
    

---

### Step 2: Create Multiple EC2 Instances ⚙️

To know about how to create EC2 instances check my blog by [clicking here](https://disarj.hashnode.dev/how-to-launch-an-ec2-instance-in-the-new-aws-console)

We’ll create two sets of instances:

* **2 instances for the Home Page (**`/`**)**
    
* **2 instances for the Test Page (**`/test`**)**
    

#### For Home Page Instances 🏠

1. Launch 2 EC2 instances.
    
2. Use the following **User Data** script:
    

```bash
#!/bin/bash
sudo yum -y update
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>My instance is running</h1>" > /var/www/html/index.html
sudo systemctl restart httpd
```

#### For Test Page Instances 🛠️

1. Launch 2 more EC2 instances.
    
2. Use this **User Data** script to create a `/test` directory:
    

```bash
#!/bin/bash
sudo yum -y update
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
sudo mkdir /var/www/html/test
echo "<h1>This is for test dir $(hostname)</h1>" > /var/www/html/test/index.html
sudo systemctl restart httpd
```

> 🔹 **Pro Tip**: Verify that the instances are up and running using their Public IPs.

---

### Step 3: Check Instance Status ✅

Make sure all 4 instances are running and accessible:

* Home Page instances: Access `http://<instance_public_ip>`
    
* Test Page instances: Access `http://<instance_public_ip>/test`
    

---

### Step 4: Create Target Groups 🎯

We need two target groups:

* `tg-home` for Home Page instances.
    
* `tg-test` for Test Page instances.
    

1. Go to the **Elastic Load Balancer** section.
    
2. Click on **Target Groups**.
    
3. Create **Target Group 1**:
    
    * Name: `tg-home`
        
    * Add the Home Page instances.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734398768575/51568bdf-8aaa-4011-a2c6-bdd6b55b35e5.png align="center")
        
4. Create **Target Group 2**:
    
    * Name: `tg-test`
        
    * Add the Test Page instances.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734398789275/481a4ee6-d979-4942-a169-81f20985bc2e.png align="center")
        

> ✅ **Success**: Both target groups are ready to handle specific traffic.

---

### Step 5: Create an Application Load Balancer 🌐

1. Follow the steps to create an **Application Load Balancer**.
    
    * If unsure, check my blog on ELB which will help you create an application load balancer [click here](https://disarj.hashnode.dev/amazon-elastic-load-balancer-a-step-by-step-guide)
        
2. While configuring the ALB, set the default target group to `tg-home`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399078202/80118639-15db-41be-9a5d-387f1dfdd76e.png align="center")
    

---

### Step 6: Add Path-Based Redirect Rules 🛤️

1. Go to the **Listeners** section of your ALB.
    
2. Select **Rules** and click on **Edit Rules**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399237030/a3667891-d0ba-4e2f-943a-7e76c0d80915.png align="center")
    
3. Add a new rule:
    
    * **Condition**: Path is `/test`.
        
    * **Action**: Forward traffic to the target group `tg-test`.
        

#### Steps to Add Rules 📝

1. Click **Add Rule**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399591971/bd6cbdd7-059e-46d5-b15c-7a3bdb5fda9b.png align="center")
    
2. Set the condition:
    
    * Choose **Path**.
        
    * Add `/test` as the value.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399607344/14ec62e3-6ae2-4088-85b0-484062e72b32.png align="center")
        
3. Set the action:
    
    * Select **Forward to** and choose `tg-test`.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399618500/a7f1b6e8-d6b7-4845-92aa-842fc2bbcea7.png align="center")
        
4. Save the rule.
    

> 🔹 The ALB will now forward `/test` traffic to the Test Page instances and all other traffic to the Home Page instances.

---

### Step 7: Test the Configuration 🔍

1. Copy the **DNS Name** of the ALB.
    
2. Open your browser and test:
    
    * `http://<ALB_DNS>` → Should load the **Home Page**.
        
    * `http://<ALB_DNS>/test` → Should load the **Test Page**.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734399640522/c78aee6c-3dc6-44b9-a524-a1fe21ba7790.png align="center")
        

> 🎉 **Success**: Path-based redirects are working perfectly!

---

## Wrapping Up 🎯

Path-based redirects in AWS ALB help you optimize traffic routing for specific URL paths. This is an essential feature for modern web applications that need to handle multiple services or microservices under one load balancer.

By following this guide, you can:

* Set up EC2 instances with specific configurations.
    
* Create target groups to organize your instances.
    
* Configure path-based rules to route traffic efficiently.
    

> 🔹 **Ready to explore more AWS features? Stay tuned for more hands-on guides!** 🚀