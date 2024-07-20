# EBS Volume Types
<hr>

### 1. General Purpose SSD (gp3 and gp2)
- **Description**: Balanced price and performance for a wide variety of workloads.
- **Use Cases**: Boot volumes, medium-sized databases, development and test environments.
- **Performance**:
  - **gp3**: Baseline performance of 3,000 IOPS, can provision up to 16,000 IOPS.
  - **gp2**: Baseline performance of 3 IOPS/GB, can burst up to 16,000 IOPS.

### 2. Provisioned IOPS SSD (io2 and io1)
- **Description**: Designed for I/O-intensive applications requiring high performance.
- **Use Cases**: Large databases, critical business applications.
- **Performance**:
  - **io2**: 99.999% durability, supports up to 64,000 IOPS.
  - **io1**: Supports up to 64,000 IOPS per volume.

### 3. Throughput Optimized HDD (st1)
- **Description**: Low-cost HDD volume designed for frequently accessed, throughput-intensive workloads.
- **Use Cases**: Big data, data warehouses, log processing.
- **Performance**: Baseline throughput of 40 MB/s per TB, can burst up to 250 MB/s per TB.

### 4. Cold HDD (sc1)
- **Description**: Lowest cost HDD volume designed for less frequently accessed workloads.
- **Use Cases**: Infrequent access data, backup, archival storage.
- **Performance**: Baseline throughput of 12 MB/s per TB, can burst up to 80 MB/s per TB.

### 5. Magnetic (standard)
- **Description**: Previous-generation HDD storage, less commonly used.
- **Use Cases**: Workloads where data is infrequently accessed.
- **Performance**: Up to 40-90 MB/s of throughput.

## How to Choose the Right EBS Volume Type
1. **Assess Your Workload**: Understand the performance requirements of your application.
2. **Consider Cost vs Performance**: Balance the cost of the volume against the required performance.
3. **Scalability Needs**: Choose a volume type that can scale with your data growth and performance needs.
4. **Durability and Availability**: Ensure the volume type meets your durability and availability requirements.

## Flow Diagram for Choosing an EBS Volume Type

flow diagram for how to choose the appropriate EBS volume type:

```plaintext
                   +-------------------------------+
                   | Assess Workload Requirements  |
                   +-------------------------------+
                                |
                                V
      +--------------------+----------------------+
      |                    |                      |
      V                    V                      V
+-------------+    +---------------+     +------------------+
| I/O Intensive|    | Throughput   |     | Infrequent Access|
|   Workloads  |    |  Intensive   |     |      Data        |
+-------------+    +---------------+     +------------------+
      |                    |                      |
      V                    V                      V
+-------------+    +---------------+     +------------------+
| Provisioned |    | Throughput    |     | Cold HDD         |
|  IOPS SSD   |    | Optimized HDD |     |   (sc1)          |
|  (io2/io1)  |    |    (st1)      |     +------------------+
+-------------+    +---------------+
      |
      V
+-------------+
| General     |
| Purpose SSD |
|  (gp3/gp2)  |
+-------------+
```


