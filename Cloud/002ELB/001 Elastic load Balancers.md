# Scalability & High Availability

- **Scalability** means that an application/system can handle greater loads by adapting.
- There are two kinds of scalability:
  - **Vertical Scalability**
  - **Horizontal Scalability** (also known as elasticity)
- Scalability is linked to but different from **High Availability**.
- Let’s deep dive into the distinction, using a call center as an example.

# Scalability & High Availability in AWS

## Scalability

**Scalability** refers to an application's or system's ability to handle increased loads by adding resources. AWS provides robust support for both vertical and horizontal scalability:

### Vertical Scalability
- **Definition**: Increasing the capacity of a single instance or server.
- **How AWS Supports It**: 
  - You can resize your EC2 instances to larger instance types.
  - Suitable for applications that are difficult to distribute across multiple instances.
  - Example: Upgrading from a t2.micro to a m5.large instance to handle more CPU or memory-intensive tasks.

### Horizontal Scalability (Elasticity)
- **Definition**: Increasing the number of instances or servers to distribute the load.
- **How AWS Supports It**: 
  - Use Auto Scaling to automatically adjust the number of EC2 instances based on demand.
  - Load Balancers (ELB) distribute incoming application traffic across multiple targets, such as EC2 instances.
  - Example: Adding more EC2 instances to handle increased web traffic during peak hours.

## High Availability

**High Availability** (HA) ensures that applications remain operational and accessible even in the face of failures. AWS offers several services and features to achieve high availability:

### Key Concepts:
- **Fault Tolerance**: The ability to remain operational even if some components fail.
- **Redundancy**: Duplication of critical components to ensure availability.

### How AWS Supports High Availability:
- **Multi-AZ Deployments**: Distribute instances across multiple Availability Zones (AZs) to protect against data center failures.
  - Example: Deploying RDS databases in Multi-AZ configurations for automatic failover.
- **Load Balancers**: ELB distributes incoming traffic across multiple instances, ensuring that the failure of one instance does not affect overall application availability.
- **Elastic IPs**: Static IP addresses that can be remapped to any instance within a region in case of failure.
- **Route 53**: A highly available and scalable DNS web service that routes end users to your application by translating domain names into IP addresses.

## Example: Call Center

Using a call center as an analogy to illustrate the concepts:

- **Scalability**:
  - **Vertical Scalability**: Adding more phone lines to a single operator.
  - **Horizontal Scalability**: Hiring more operators to handle increased call volumes.

- **High Availability**:
  - Ensuring multiple operators are available so that if one is unavailable, others can take calls.
  - Having backup power and communication lines to keep the call center operational during outages.

## Summary

AWS provides powerful tools and services to achieve both scalability and high availability. By leveraging these services, you can ensure your applications handle increased loads efficiently and remain operational even in the event of component failures.
