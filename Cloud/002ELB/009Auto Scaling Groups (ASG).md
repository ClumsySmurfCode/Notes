# Auto Scaling Groups (ASG) 

## Overview
Auto Scaling Groups (ASG) in AWS are a critical feature that helps maintain application availability and allows you to automatically add or remove EC2 instances based on defined policies, schedules, and health checks. ASGs help ensure that you have the right number of EC2 instances available to handle the load for your application.

![image](https://github.com/user-attachments/assets/4b554f0c-a536-4a0b-ab60-629ac55fe35c)


## Key Features
- **Automatic Scaling**: Automatically adjusts the number of EC2 instances to handle the load.
- **Health Checks**: Monitors the health of instances and replaces unhealthy instances.
- **Scaling Policies**: Configurable policies based on metrics such as CPU utilization, network traffic, etc.
- **Scheduled Scaling**: Ability to scale in and out at specific times based on predictable traffic patterns.
- **High Availability**: Distributes instances across multiple Availability Zones (AZs) to ensure high availability.

## Components of Auto Scaling Groups
1. **Launch Configuration/Template**: Specifies the instance type, Amazon Machine Image (AMI), key pair, security groups, and other parameters for launching new instances.
2. **Auto Scaling Group**: The group itself, which contains the EC2 instances.
3. **Scaling Policies**: Rules that define when and how the ASG should scale the number of instances.

## How Auto Scaling Works
1. **Define Launch Configuration/Template**: Create a launch configuration or template that specifies the instance details.
2. **Create Auto Scaling Group**: Define an ASG that uses the launch configuration/template and specify the desired number of instances, minimum, and maximum instance counts.
3. **Set Scaling Policies**: Configure scaling policies that dictate when to add or remove instances based on CloudWatch alarms.
4. **Health Checks**: ASG monitors the health of instances and replaces any that fail health checks.
5. **Scaling Actions**: Based on policies and health checks, the ASG automatically scales the number of instances up or down.

## Flow Diagram for Auto Scaling Groups

```plaintext
+----------------------------+
| Define Launch Configuration|
| or Template                |
+------------+---------------+
             |
             V
+------------+---------------+
| Create Auto Scaling Group  |
| (Min, Max, Desired Count)  |
+------------+---------------+
             |
             V
+------------+---------------+
| Set Scaling Policies       |
| (CloudWatch Alarms)        |
+------------+---------------+
             |
             V
+------------+---------------+
| Monitor Health Checks      |
+------------+---------------+
             |
             V
+------------+---------------+
| Perform Scaling Actions    |
| (Add/Remove Instances)     |
+----------------------------+
```

## Benefits
- **Cost Management**: Helps in optimizing costs by scaling in during low demand and scaling out during high demand.
- **Reliability**: Increases the reliability and availability of your application by ensuring that you always have the right number of instances.
- **Flexibility**: Offers flexibility to scale based on various metrics and schedules.

-----

## What’s an Auto Scaling Group?

- In real life, the load on your websites and application can change.
- In the cloud, you can create and get rid of servers very quickly.

### The goal of an Auto Scaling Group (ASG) is to:
- Scale out (add EC2 instances) to match an increased load.
- Scale in (remove EC2 instances) to match a decreased load.
- Ensure we have a minimum and a maximum number of EC2 instances running.
- Automatically register new instances to a load balancer.
- Re-create an EC2 instance in case a previous one is terminated (e.g., if unhealthy).
- ASGs are free (you only pay for the underlying EC2 instances).

![image](https://github.com/user-attachments/assets/eb69edad-da27-472b-9c41-5ae5105be952)

![image](https://github.com/user-attachments/assets/a5e9b908-461f-4b11-a2c0-00d54ac9011e)


## Auto Scaling Groups – Scaling Policies

### Dynamic Scaling

#### Target Tracking Scaling
- Simple to set up.
- Example: I want the average ASG CPU to stay at around 40%.

#### Simple / Step Scaling
- When a CloudWatch alarm is triggered (example: CPU > 70%), then add 2 units.
- When a CloudWatch alarm is triggered (example: CPU < 30%), then remove 1 unit.

### Scheduled Scaling
- Anticipate scaling based on known usage patterns.
- Example: increase the minimum capacity to 10 at 5 pm on Fridays.


## A Launch Template (older “Launch Configurations” are deprecated)

### Components
- **AMI + Instance Type**: Specifies the Amazon Machine Image and the type of EC2 instance to launch.
- **EC2 User Data**: Scripts and commands to run on instance startup.
- **EBS Volumes**: Configuration for Elastic Block Store volumes attached to the instance.
- **Security Groups**: Firewall rules that control inbound and outbound traffic.
- **SSH Key Pair**: Key pair for SSH access to the instances.
- **IAM Roles for your EC2 Instances**: Permissions and roles assigned to instances for accessing other AWS services.
- **Network + Subnets Information**: Specifies the VPC, subnets, and networking settings.
- **Load Balancer Information**: Configuration details for attaching instances to a load balancer.
- **Min Size / Max Size / Initial Capacity**: Defines the minimum, maximum, and initial number of instances in the Auto Scaling Group.
- **Scaling Policies**: Rules for scaling the number of instances up or down based on demand.

![image](https://github.com/user-attachments/assets/9ef8978d-1681-4a0e-88d2-d355a84acefa)


## Auto Scaling - CloudWatch Alarms & Scaling

- **It is possible to scale an ASG based on CloudWatch alarms.**
- **An alarm monitors a metric** (such as Average CPU, or a custom metric).
- **Metrics** such as Average CPU are computed for the overall ASG instances.

### Based on the alarm:
- We can create **scale-out policies** (increase the number of instances).
- We can create **scale-in policies** (decrease the number of instances).

![image](https://github.com/user-attachments/assets/1b21cc20-1b72-4d72-aad9-a39bffbac2d6)


## Auto Scaling Groups – Scaling Policies

### Dynamic Scaling

#### Target Tracking Scaling
- **Simple to set up**
- **Example**: I want the average ASG CPU to stay at around 40%

#### Simple / Step Scaling
- When a CloudWatch alarm is triggered (example: CPU > 70%), then add 2 units
- When a CloudWatch alarm is triggered (example: CPU < 30%), then remove 1 unit

### Scheduled Scaling
- **Anticipate scaling based on known usage patterns**
- **Example**: Increase the minimum capacity to 10 at 5 pm on Fridays


## Auto Scaling Groups – Scaling Policies
- Predictive scaling: continuously forecast load and schedule scaling ahead
  
![image](https://github.com/user-attachments/assets/cb8fe7bf-1aa5-4ea1-8032-06b6fb03f97c)


## Good Metrics to Scale On

- **CPUUtilization**: Average CPU utilization across your instances
- **RequestCountPerTarget**: To make sure the number of requests per EC2 instance is stable
- **Average Network In / Out**: Useful if your application is network bound
- **Any custom metric**: Metrics that you push using CloudWatch

![image](https://github.com/user-attachments/assets/b4dda322-3a88-4ed8-8501-7a17111fb423)


## Auto Scaling Groups - Scaling Cooldowns

- **Cooldown Period**: After a scaling activity happens, you enter a cooldown period (default 300 seconds).
- **Purpose**: During the cooldown period, the ASG will not launch or terminate additional instances to allow for metrics to stabilize.
- **Advice**: Use a ready-to-use AMI to reduce configuration time, serve requests faster, and reduce the cooldown period.

![image](https://github.com/user-attachments/assets/5e8046ed-74d8-4063-ac8b-bfd9e047fde1)
