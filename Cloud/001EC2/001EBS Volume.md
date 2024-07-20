#  Amazon Elastic Block Store (EBS)
### Overview
Amazon Elastic Block Store (EBS) is a cloud-based storage service provided by Amazon Web Services (AWS) that offers persistent block storage volumes for use with Amazon EC2 instances. EBS is designed for applications that require a database, file system, or raw block storage.

###  Component Diagram 
![image](https://github.com/user-attachments/assets/4d229ee9-e911-4bf8-9ef2-43d59b6de6f3)

Description of the Diagram
- Amazon EC2 <-> Amazon EBS: EC2 instances are associated with EBS volumes. An EC2 instance can attach one or more EBS volumes.
- Amazon EBS <-> AWS Availability Zone: EBS volumes are automatically replicated within the same Availability Zone to provide high availability and durability.
- Amazon EBS <-> AWS S3: EBS volumes can create snapshots that are stored in Amazon S3.
- Amazon EBS <-> AWS KMS: EBS uses AWS KMS for managing encryption keys, providing encryption for data at rest and in transit.

## Components:
- Amazon EBS: The primary component representing the EBS service.
- Amazon EC2: Represents EC2 instances that use EBS volumes.
- AWS Availability Zone: Represents the AZs where EBS volumes are replicated.
- AWS S3: Represents the storage service used for EBS snapshots.
- AWS KMS: Represents the Key Management Service used for encryption.
- Relationships:
- Association: Shows the relationship between EC2 instances and EBS volumes.
- Dependency: Shows the dependency of EBS on AWS S3 for snapshots and AWS KMS for encryption.

## Visual Representation

![image](https://github.com/user-attachments/assets/a8bcec1f-ff14-4b49-a8a0-a7b44740c8e2)

```
When creating EC2 instances, you can only use the following EBS volume types as boot volumes:
gp2, gp3, io1, io2, and Magnetic (Standard).
```

### Key Features

### `Persistent Storage:`

EBS volumes are persistent, meaning data is retained even after the EC2 instance is terminated.
Suitable for data that must be quickly accessible and requires long-term persistence.

### `Scalability:`

EBS volumes can be dynamically resized up to 16 TiB, allowing for easy scaling as storage requirements grow.
Offers the flexibility to modify volume type, size, and performance without downtime.

### `Performance Options:`

General Purpose SSD (gp3/gp2): Cost-effective, balanced performance.:`
Provisioned IOPS SSD (io2/io1): High performance, designed for critical applications requiring low-latency and high throughput.
Throughput Optimized HDD (st1): Low-cost, high-throughput storage for frequently accessed, large, sequential workloads.
Cold HDD (sc1): Lowest cost, designed for less frequently accessed workloads.

### `Availability and Durability:`

EBS volumes are automatically replicated within their Availability Zone to protect against hardware failures.
Designed for an annual failure rate of 0.1%-0.2%.

### `Backup and Restore:`

Supports creating point-in-time snapshots of EBS volumes.
Snapshots are stored in Amazon S3 and can be used to create new EBS volumes or restore existing ones.

### `Encryption:`

EBS offers encryption to protect data at rest, data in transit between instances and volumes, and snapshots.
Integrated with AWS Key Management Service (KMS) for managing encryption keys.

### `Cost-Effective:`

Pay-as-you-go pricing model, only pay for the storage you provision.
Different volume types cater to various performance and cost needs, optimizing spend based on workload requirements.

## Use Cases
- Databases: High-performance storage for relational and non-relational databases.
- Enterprise Applications: Block storage for critical applications like SAP and Microsoft Exchange.
- Big Data Analytics: High throughput storage for Hadoop, Spark, and other data processing frameworks.
- Backup and Recovery: Reliable and durable storage for backups and disaster recovery solutions.

## Benefits
- High Availability: EBS volumes can be attached to EC2 instances in the same Availability Zone, ensuring high availability.
- Flexible and Scalable: Easy to adjust storage capacity and performance characteristics on the fly.
- Secure: Robust security features, including encryption and integration with IAM for access control.
- Cost Efficiency: Optimized pricing models for various performance levels, ensuring cost-effective storage solutions.



![image](https://github.com/user-attachments/assets/5dd234a7-dbde-4bb6-b2d0-0d7c583c0224)


![image](https://github.com/user-attachments/assets/e2b43957-c2b5-49a3-a012-166b9d698052)


![image](https://github.com/user-attachments/assets/e98e036e-e725-4e41-8f7c-aca6634029aa)


