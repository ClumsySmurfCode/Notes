# AWS EC2 Instance Store

## What is an EC2 Instance Store?
AWS EC2 Instance Store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances.

## Key Features
1. **Temporary Storage**: Data is lost when the instance stops, terminates, or fails.
2. **High I/O Performance**: Instance store provides very high random I/O performance and low latency.
3. **No Additional Cost**: Instance storage is included in the cost of the EC2 instance.
4. **Physical Storage**: Located on disks that are physically attached to the host computer.

## Use Cases
1. **Cache or Buffer Storage**: Storing temporary data like caches or buffers.
2. **Scratch Data**: Storing temporary data needed for the operation of applications.
3. **Replicated Data**: Data that can be easily reproduced or replicated across multiple instances.

## EC2 Instance Store Lifecycle
1. **Launch Instance**: Launch an EC2 instance with instance store-backed volumes.
2. **Attach Instance Store**: Instance store volumes are automatically attached to the instance.
3. **Data Storage**: Use instance store for temporary data storage during the instance's lifetime.
4. **Termination**: Data on instance store volumes is lost when the instance is stopped or terminated.

## Flow Diagram

Here’s a flow diagram to illustrate the process of using AWS EC2 Instance Store:

```plaintext
 +---------------------+
 |    Launch Instance  |
 +---------+-----------+
           |
           V
 +---------+-----------+
 | Attach Instance Store|
 +---------+-----------+
           |
           V
 +---------+-----------+
 |   Data Storage      |
 +---------+-----------+
           |
           V
 +---------+-----------+
 |  Termination or Stop|
 +---------------------+
           |
           V
 +---------+-----------+
 |  Data Lost on       |
 |  Instance Store     |
 +---------------------+
```

``` ## Description of the Flow Diagram

This document outlines the workflow for using instance stores in Amazon Web Services (AWS).

## Launch Instance

* Start by launching an EC2 instance that includes instance store-backed volumes.
## Attach Instance Store

* The instance store volumes are automatically attached to the instance upon launch.

## Data Storage
* Use the instance store for storing temporary data during the instance's operation.

## Termination or Stop
**Important:** When the instance is terminated or stopped, the data stored in the instance store is lost.

## Data Lost on Instance Store
* Since instance store volumes are ephemeral, any data stored on them is lost when the instance stops, terminates, or fails.
```

# How to Use Instance Store in AWS
Here's a step-by-step guide on leveraging instance stores:

### Launch an Instance:
*. Go to the EC2 dashboard and launch an instance.
* Choose an instance type that supports instance store volumes.

### Configure Instance Store:
* During instance configuration, add instance store volumes under "Add Storage."

### Access Instance Store:
* Once the instance is running, instance store volumes can be accessed just like any other disk.

### Monitor Instance Store:
* Regularly monitor and back up necessary data since it will be lost on termination or stop of the instance.


