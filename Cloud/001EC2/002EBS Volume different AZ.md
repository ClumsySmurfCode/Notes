## Overview 

Amazon EBS volumes are designed to be used within a single Availability Zone (AZ) due to the high-speed, low-latency requirements of block storage. However, there are scenarios where you might need to replicate or move EBS volumes across different AZs, typically for disaster recovery, backup, or migration purposes.

### Concept of EBS Volume Replication Across Different AZs
#### `Key Points:`
- Snapshots: EBS volumes cannot be directly attached to instances in a different AZ. Instead, you take snapshots of the volume, which are stored in Amazon S3.
- Restoration: You can then restore these snapshots to create new EBS volumes in a different AZ.
- Steps to Replicate EBS Volumes Across Different AZs
- Create a Snapshot: Take a snapshot of the existing EBS volume.
- Copy Snapshot: Optionally copy the snapshot to a different region (if required).
- Create New Volume: Use the snapshot to create a new EBS volume in the desired AZ.

#### `Sequence Diagram`
![image](https://github.com/user-attachments/assets/d4074f8c-a67a-448d-93c3-20a3a6091f51)

> Components:
- User: Initiates the process.
- EBS Volume (AZ1): The source EBS volume in the original AZ.
- EBS Snapshot: The snapshot created from the source EBS volume.
- Amazon S3: Storage service where snapshots are stored.
- EBS Volume (AZ2): The new EBS volume created in the target AZ.

![image](https://github.com/user-attachments/assets/85aeb700-dc43-4ccb-9e53-518b20b9eb9b)

## Description of the Process:
- User initiates the process by creating a snapshot of the EBS Volume (AZ1).
- EBS Volume (AZ1) sends a snapshot request to EBS Snapshot service.
- EBS Snapshot stores the snapshot in Amazon S3.
- The snapshot is now available in Amazon S3.
- User requests to create a new volume in EBS Volume (AZ2) using the stored snapshot.
- Amazon S3 provides the snapshot data to create the EBS Volume (AZ2) in the new AZ.


#### Steps to Implement in AWS Console:
 > Create Snapshot:

    - Go to the EC2 Dashboard.
    - Select "Volumes" from the left-hand menu.
    - Select the volume you want to replicate and click "Actions" -> "Create Snapshot".
    - Provide a description and create the snapshot.
  
  > Copy Snapshot (Optional for cross-region):

    - Go to the "Snapshots" section in the EC2 Dashboard.
    - Select the snapshot and click "Actions" -> "Copy".
    - Choose the destination region (if needed) and copy the snapshot.
  
  > Create Volume from Snapshot:

    - Go to the "Snapshots" section.
    - Select the snapshot and click "Actions" -> "Create Volume".
    - Choose the desired AZ for the new volume.
    - Specify volume type and size, and create the volume.
