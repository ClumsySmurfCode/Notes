# Cross-Zone Load Balancing

## Overview
Cross-Zone Load Balancing is a feature available in AWS Elastic Load Balancing that allows load balancers to evenly distribute traffic across all registered targets in all enabled Availability Zones (AZs). This ensures that traffic is not limited to a single AZ, providing improved fault tolerance and efficient resource utilization.

## Key Features
- **Even Traffic Distribution**: Distributes incoming traffic evenly across all targets in all enabled AZs.
- **Improved Fault Tolerance**: Enhances fault tolerance by ensuring that traffic is not concentrated in a single AZ.
- **Efficient Resource Utilization**: Maximizes the utilization of resources by balancing the load across multiple AZs.

## Benefits
- **High Availability**: Increases the availability of your application by ensuring that traffic is balanced across multiple AZs.
- **Reduced Latency**: Helps in reducing latency by distributing the load more evenly.
- **Cost-Effective**: More efficient utilization of resources can lead to cost savings.

## How Cross-Zone Load Balancing Works
1. **Incoming Traffic**: User requests arrive at the load balancer.
2. **Load Balancer Distribution**: The load balancer distributes the incoming requests evenly across all registered targets in all enabled AZs.
3. **Target Response**: The targets process the requests and send responses back to the load balancer.
4. **Response to Client**: The load balancer forwards the responses back to the clients.

## Flow Diagram for Cross-Zone Load Balancing

```plaintext
+---------------------+
|    Client Requests  |
+----------+----------+
           |
           V
+----------+----------+
| Load Balancer (ELB) |
+----------+----------+
           |
           V
+----------+----------+
| Distribute Requests |
+----------+----------+
           |
           V
+---------------------+        +---------------------+
| Target Group in AZ1 | <----> | Target Group in AZ2 |
| (Instances, etc.)   |        | (Instances, etc.)   |
+---------------------+        +---------------------+
           |
           V
+---------------------+
| Target Group in AZ3 |
| (Instances, etc.)   |
+---------------------+
```

## Description of the Flow Diagram

1. **Client Requests**: User requests arrive at the ELB.
2. **Load Balancer (ELB)**: The ELB distributes the incoming requests.
3. **Distribute Requests**: ELB evenly distributes requests across all registered targets in all enabled AZs.
4. **Target Groups**: Target groups in different AZs (e.g., AZ1, AZ2, AZ3) receive and process the requests.

![image](https://github.com/user-attachments/assets/3910e85c-b6b6-41ed-b03d-baba46b87ddc)

## Application Load Balancer
- Enabled by default (can be disabled at the Target Group level)
- No charges for inter-AZ data

## Network Load Balancer & Gateway Load Balancer
- Disabled by default
- You pay charges ($) for inter-AZ data if enabled

## Classic Load Balancer
- Disabled by default
- No charges for inter-AZ data if enabled
