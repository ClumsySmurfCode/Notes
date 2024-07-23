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

