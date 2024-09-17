### 📖 **Table of Contents**

1. [Elasticity in AWS EC2](#elasticity-in-aws-ec2)
2. [Horizontal and Vertical Scalability](#horizontal-and-vertical-scalability)
3. [Auto Scaling](#auto-scaling)
4. [High Availability](#high-availability)
5. [AMI Overview (Amazon Machine Image)](#ami-overview-amazon-machine-image)
6. [Assignments](#assignments)

---

## 📌 **Elasticity in AWS EC2**

**Elasticity** is the ability of a system to automatically adapt to workload changes by provisioning and deprovisioning resources in real-time. In AWS, elasticity allows you to automatically scale EC2 instances up or down based on the current demand, ensuring optimal performance and cost efficiency.

### **Key Points:**

- **Dynamic Resource Allocation**: AWS EC2 can dynamically add or remove instances based on demand.
- **Cost Efficiency**: Only pay for the resources you use; no need to provision for peak load continuously.
- **Performance Optimization**: Automatically adjusts resources to ensure applications run smoothly under varying load conditions.

### **Example:**

Consider a scenario where you run an e-commerce website on AWS EC2. During holiday sales, the traffic to your website spikes significantly. With elasticity, AWS automatically adds more EC2 instances to handle the increased traffic. After the sales period, as traffic reduces, the number of instances automatically scales down, saving costs by releasing unnecessary resources.

### **How to Achieve Elasticity in AWS EC2:**

1. **Auto Scaling Groups**: Automatically manage the number of EC2 instances in a fleet based on defined conditions.
2. **Elastic Load Balancing (ELB)**: Distributes incoming application traffic across multiple instances to ensure fault tolerance and high availability.

---

## 🌍 **Horizontal and Vertical Scalability**

**Scalability** refers to a system's ability to handle growth, be it increased traffic, data volume, or computational demand.

### **Horizontal Scalability (Scaling Out):**

- **Definition**: Adding more instances or servers to distribute the workload across multiple systems.
- **Advantages**:
  - Increases capacity without needing more powerful hardware.
  - Provides redundancy and fault tolerance; failure of one instance does not impact others.
- **Example**: Adding more EC2 instances behind a load balancer to handle increased web traffic.

### **Vertical Scalability (Scaling Up):**

- **Definition**: Increasing the capacity of a single instance by upgrading its resources, such as CPU, memory, or storage.
- **Advantages**:
  - Simplifies architecture by reducing the number of instances.
  - Suitable for applications that require more powerful single-instance performance.
- **Example**: Changing an EC2 instance type from `t2.micro` to `m5.large` to handle more significant processing loads.

### **Comparison Table:**

| Feature                     | Horizontal Scalability                       | Vertical Scalability                        |
|-----------------------------|----------------------------------------------|---------------------------------------------|
| **Definition**              | Adding more instances                        | Increasing resources of a single instance   |
| **Cost**                    | Typically lower initial cost, scales with instances | Higher initial cost, may be limited by hardware |
| **Performance**             | Distributes load, suitable for stateless applications | Higher single-instance performance          |
| **Fault Tolerance**         | High                                          | Low (single point of failure)               |
| **Use Case**                | Web servers, microservices                   | Databases, monolithic applications          |

### **Example Scenario:**

A social media platform sees a steady increase in user traffic. Initially, it scales vertically by upgrading its EC2 instance type. However, as traffic continues to grow, it switches to horizontal scaling by adding more instances behind an Elastic Load Balancer to distribute traffic evenly.

---

## 🚀 **Auto Scaling**

**Auto Scaling** in AWS is a service that automatically adjusts the number of EC2 instances in an application based on current demand. It ensures that the right amount of resources are available at any time.

### **Key Components:**

1. **Auto Scaling Groups (ASG)**: A collection of EC2 instances treated as a logical grouping for automatic scaling and management.
2. **Scaling Policies**: Rules that define when to add or remove instances based on metrics like CPU utilization, network traffic, or custom metrics.
3. **Launch Configuration/Launch Template**: Specifies the instance configuration (AMI, instance type, security groups, etc.) for new instances in the Auto Scaling Group.

### **Example of Auto Scaling Use Case:**

- An online gaming platform experiences fluctuating user loads throughout the day. By using Auto Scaling, the platform can dynamically add more instances during peak times and scale down during off-peak times, optimizing costs and maintaining performance.

### **Types of Auto Scaling:**

1. **Dynamic Scaling**: Responds to changing demand in real-time based on predefined scaling policies.
2. **Scheduled Scaling**: Scales in response to predictable changes, like scheduled events or known patterns.
3. **Predictive Scaling**: Uses machine learning models to forecast demand and adjust capacity proactively.

---

## ⚡ **High Availability**

**High Availability (HA)** in AWS refers to designing systems that are resilient and available for use with minimal downtime. It ensures that applications are always accessible, even in the event of hardware or software failures.

### **Key Concepts:**

- **Multi-AZ Deployment**: Distributing resources across multiple Availability Zones within a region to provide redundancy.
- **Load Balancing**: Using services like ELB (Elastic Load Balancing) to distribute traffic across multiple healthy instances.
- **Failover and Recovery**: Implementing automated recovery strategies to quickly replace failed instances.

### **Example:**

A critical banking application is deployed across multiple AZs in the AWS region. An ELB is configured to distribute incoming traffic evenly across instances. If one instance or AZ fails, the traffic is redirected to other healthy instances without downtime.

---

## 🖥️ **AMI Overview (Amazon Machine Image)**

**Amazon Machine Image (AMI)** is a pre-configured template that contains the software configuration (OS, application server, and applications) required to launch an EC2 instance.

### **Key Features:**

- **Custom Images**: Users can create their own AMIs to standardize deployments across multiple instances.
- **Public and Private AMIs**: AWS provides publicly available AMIs, while users can also create private AMIs.
- **Shared AMIs**: AMIs can be shared across accounts or made available in the AWS Marketplace.

### **How to Create an AMI:**

1. **Launch an Instance**: Start with a base instance and configure it with the desired software and settings.
2. **Create an AMI**: From the AWS Management Console, navigate to EC2 > Instances, select the instance, and choose "Create Image".
3. **Configure Image Settings**: Provide a name and description for the AMI, select storage options, and create the image.
4. **Use the AMI**: The new AMI can be used to launch instances with the same configuration.

### **Example Use Case:**

- A company has a standard web server configuration for all its projects. By creating a custom AMI, they can quickly deploy new EC2 instances with the exact configuration, reducing setup time and maintaining consistency across environments.

---
