### AWS VPC Fundamentals

Amazon Virtual Private Cloud (VPC) allows you to launch AWS resources in a virtual network that you define. This virtual network closely resembles a traditional network that you might operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

#### Key Components of a VPC

1. **Subnets**:
   - **Public Subnets**: Subnets that have a route to the internet via an internet gateway.
   - **Private Subnets**: Subnets that do not have a route to the internet. Often used for backend systems.

2. **Internet Gateway (IGW)**:
   - Enables communication between instances in your VPC and the internet.

3. **NAT Gateway/Instance**:
   - Allows instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating connections with those instances.

4. **Route Tables**:
   - Controls the traffic routing for subnets. Each subnet must be associated with a route table.

5. **Network Access Control Lists (NACLs)**:
   - Provides stateless filtering of ingress and egress traffic for subnets.

6. **Security Groups**:
   - Provides stateful filtering of ingress and egress traffic for instances.

7. **Peering Connections**:
   - Allows VPCs to communicate with each other as if they are within the same network.

8. **VPC Endpoints**:
   - Enables private connection between your VPC and supported AWS services without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection.

#### VPC Setup Flow Diagram

Below is a flow diagram illustrating the basic setup of a VPC:

```plaintext
                             +---------------------------+
                             |        VPC                |
                             |                           |
                             | +-------+   +-------+     |
                             | |SubNet1|   |SubNet2|     |
                             | |Public |   |Private|     |
                             | +---+---+   +---+---+     |
                             |     |           |         |
+---------------+            |     |           |         |
|Internet       | <---------+|+----v-----------v----+   |
|Gateway        |            ||       Route Table   |   |
+---------------+            ||    (Routing Rules)  |   |
                             |+----+-----------+----+   |
                             |     |           |        |
                             |     |           |        |
                             |+----v-----------v----+   |
                             ||       NACLs          |  |
                             |+----+-----------+----+   |
                             |     |           |        |
                             |     |           |        |
                             |+----v-----------v----+   |
                             ||     Security Groups  |  |
                             +------------------------+
```

### NACL, SG, VPC Flow Logs

Amazon VPC (Virtual Private Cloud) provides several features to enhance the security and monitoring of your AWS resources, including Network Access Control Lists (NACLs), Security Groups (SGs), and VPC Flow Logs.

#### Network Access Control Lists (NACLs)

- **Stateless Filtering**: NACLs provide stateless filtering of traffic at the subnet level.
- **Inbound and Outbound Rules**: You can define both inbound and outbound rules. Each rule is evaluated in the order in which it's listed.
- **Rules Evaluation**: Each rule can either allow or deny traffic. NACLs evaluate rules in order from lowest to highest, and once a rule matches, it's applied and the rest are ignored.
- **Applicable to Subnets**: NACLs are associated with one or more subnets.

#### Security Groups (SGs)

- **Stateful Filtering**: Security groups provide stateful filtering of traffic at the instance level.
- **Allow Rules Only**: Security groups support allow rules only, making them easier to manage.
- **Automatic Inbound Response**: When you allow outbound traffic, the corresponding inbound response traffic is automatically allowed.
- **Attached to Instances**: Security groups are attached to instances, and you can attach multiple security groups to a single instance.

#### VPC Flow Logs

- **Traffic Capture**: VPC Flow Logs capture detailed information about the traffic going to and from network interfaces in your VPC.
- **Log Storage**: Flow log data can be published to Amazon CloudWatch Logs or Amazon S3.
- **Use Cases**: Useful for monitoring traffic, troubleshooting connectivity issues, and forensics.
- **Filter Options**: You can create flow logs for a VPC, a subnet, or a network interface.

### Flow Diagram

Below is a flow diagram illustrating the relationship and functionality of NACLs, Security Groups, and VPC Flow Logs within a VPC:

```plaintext
                            +---------------------------+
                            |           VPC             |
                            |                           |
                            | +-----------------------+ |
                            | |         Subnet        | |
                            | |                       | |
                            | |  +-----------------+  | |
                            | |  |  NACL           |  | |
                            | |  | (Stateless)     |  | |
                            | |  +--------+--------+  | |
                            | |           |           | |
                            | |  +--------v--------+  | |
                            | |  | Security Groups |  | |
                            | |  |   (Stateful)    |  | |
                            | |  +--------+--------+  | |
                            | |           |           | |
                            | |  +--------v--------+  | |
                            | |  |    Instances    |  | |
                            | |  +-----------------+  | |
                            | +-----------------------+ |
                            +---------------------------+
                                      |
                                      v
                             +------------------+
                             | VPC Flow Logs    |
                             | (Monitoring)     |
                             |                  |
                             | CloudWatch Logs  |
                             |       or         |
                             | Amazon S3        |
                             +------------------+
```


### VPC Peering

Amazon Virtual Private Cloud (VPC) Peering allows you to connect one VPC with another via a direct network route using private IP addresses. Instances in either VPC can communicate with each other as if they are within the same network. This feature is especially useful for simplifying network configurations and enabling resource sharing between VPCs.

#### Key Features of VPC Peering

- **Private Communication**: VPC Peering provides a secure, private connection between VPCs using private IP addresses.
- **Same or Different AWS Accounts**: VPCs in the peering connection can be in the same AWS account or different AWS accounts.
- **Same or Different Regions**: VPC Peering connections can be established within the same region (intra-region) or across different regions (inter-region).
- **No Overlapping CIDR**: The CIDR blocks of the VPCs in a peering connection must not overlap.
- **No Transitive Peering**: Peering connections are non-transitive; you must establish a peering connection between each VPC pair that needs to communicate.

### Use Cases

- **Cross-Account Communication**: Facilitate communication between VPCs owned by different AWS accounts.
- **Resource Sharing**: Share resources such as databases and applications between different VPCs.
- **Simplified Network Configuration**: Simplify the network topology by using VPC Peering instead of complex VPN or Direct Connect configurations.

### Flow Diagram

Below is a flow diagram illustrating how VPC Peering works:

```plaintext
+----------------------+                +----------------------+
|        VPC A         |                |        VPC B         |
|                      |                |                      |
|  +----------------+  |  VPC Peering   |  +----------------+  |
|  |    Subnet A1   |  |<-------------->|  |    Subnet B1   |  |
|  +----------------+  |                |  +----------------+  |
|                      |                |                      |
|  +----------------+  |                |  +----------------+  |
|  |    Subnet A2   |  |                |  |    Subnet B2   |  |
|  +----------------+  |                |  +----------------+  |
|                      |                |                      |
+----------------------+                +----------------------+
```

### Step-by-Step Process

1. **Create VPCs**: Create two VPCs with non-overlapping CIDR blocks.
2. **Initiate Peering Connection**: Initiate a peering connection request from one VPC (Requester) to the other VPC (Accepter).
3. **Accept Peering Connection**: Accept the peering connection request from the Accepter VPC.
4. **Update Route Tables**: Update the route tables of each VPC to include routes that direct traffic to the peered VPC.
5. **Configure Security Groups**: Modify the security groups to allow traffic from the peered VPC.


## Three Tier architecture 

![image](https://github.com/user-attachments/assets/aab5420b-56c6-409f-99a7-2bfa8d2e29dc)
