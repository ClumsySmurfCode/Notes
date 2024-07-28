# Route 53 – Routing Policies

Amazon Route 53 is a scalable Domain Name System (DNS) web service designed to route end-user requests to the appropriate endpoints. It offers various routing policies to control how traffic is routed to resources based on specific requirements. Here are the primary routing policies available in Route 53:

- **Define how Route 53 responds to DNS queries**
  - Don’t get confused by the word “Routing”
  - It’s not the same as Load Balancer routing which routes the traffic
  - DNS does not route any traffic, it only responds to the DNS queries

- **Route 53 Supports the following Routing Policies:**
  - **Simple**
  - **Weighted**
  - **Failover**
  - **Latency based**
  - **Geolocation**
  - **Multi-Value Answer**
  - **Geoproximity** (using Route 53 Traffic Flow feature)

### `Simple Routing Policy`

#### Overview
- **Use Case**: When you have a single resource that performs a given function for your domain (e.g., one web server serving content for a website).
- **Functionality**: Returns one IP address or other records in response to DNS queries.
![image](https://github.com/user-attachments/assets/c3edebfd-a87a-4953-b4b7-3883ab213cde)

#### Example
If a DNS query is made for `example.com`, it returns the IP address of your single web server.


### `Weighted Routing Policy`

### Weighted Routing Policy in Route 53

- **Control the percentage of the requests that go to each specific resource**
  - Assign each record a relative weight:
    - (weight_formula.png) \( \text{Weight (%) = } \frac{\text{Weight of a specific record}}{\text{Sum of weights for all records}} \)
  - Weights don’t need to sum up to 100
  - DNS records must have the same name and type
  - Can be associated with Health Checks
  - **Use cases:**
    - Load balancing between regions
    - Testing new application versions
  - Assign a weight of 0 to a record to stop sending traffic to a resource
  - If all records have a weight of 0, then all records will be returned equally

#### Overview
- **Use Case**: When you want to distribute traffic across multiple resources in specific proportions.
- **Functionality**: Assigns weights to resource records to specify the proportion of traffic routed to each resource.

![image](https://github.com/user-attachments/assets/d7480210-8fa3-41de-818f-084bd42de1c0)

#### Example
If you have two web servers and you want 70% of traffic to go to the first server and 30% to the second, you set weights accordingly (e.g., 70 and 30).

### `Latency Routing Policy`

- **Redirect to the resource that has the least latency close to us**
  - **Super helpful when latency for users is a priority**
  - **Latency is based on traffic between users and AWS Regions**
  - Example: Germany users may be directed to the US (if that’s the lowest latency)
  - **Can be associated with Health Checks** (has a failover capability)
#### Overview
- **Use Case**: When you have resources in multiple locations and want to route traffic based on the lowest network latency for the user.
- **Functionality**: Routes traffic to the resource that provides the best latency (minimum round trip time).

![image](https://github.com/user-attachments/assets/a7e5d606-e965-407c-aa9f-88a3d79404db)

#### Example
If a user in Europe queries your domain, Route 53 routes the request to the European server because it has the lowest latency for that user.

### `Failover Routing Policy`  

The **Failover Routing Policy** in Amazon Route 53 is used to create an active-passive failover configuration. This ensures that traffic is routed to a primary resource when it is healthy and automatically fails over to a secondary resource if the primary becomes unhealthy.
![image](https://github.com/user-attachments/assets/ef0bffe2-6957-4446-8940-830a6cdc283e)

- **Primary and Secondary Resources**:
  - **Primary Resource**: The main resource to which traffic is routed under normal conditions.
  - **Secondary Resource**: The backup resource that receives traffic when the primary resource fails.

- **Health Checks**:
  - Health checks are essential for failover routing to monitor the health of the primary and secondary resources.
  - Route 53 will only route traffic to resources that are deemed healthy based on the health checks.

### `Route 53 Health Checks`
- **Use Case**: For configuring active-passive failover.
- **Functionality**: Routes traffic to a primary resource unless it is unavailable, then fails over to a secondary resource.

![image](https://github.com/user-attachments/assets/ed29651d-05e3-4b1d-9cc4-52440dc3b5cf)
    
#### HTTP Health Checks
    
  - **Scope**: Only for public resources
  - **Usage**: Automate DNS Failover
    
#### Automated DNS Failover
    
   1. **Health Checks that Monitor an Endpoint**:
      - Monitors applications, servers, or other AWS resources.
   2. **Health Checks that Monitor Other Health Checks (Calculated Health Checks)**:
      - Aggregates the results of multiple health checks to determine overall health.
  3. **Health Checks that Monitor CloudWatch Alarms**:
      - Provides full control and flexibility.
      - Useful for monitoring:
      - Throttles of DynamoDB
      - Alarms on RDS
      - Custom metrics
      - Other private resources
#### Integration with CloudWatch
    - **CloudWatch Metrics**:
    - Health checks are integrated with CloudWatch metrics for monitoring and alerting.
![image](https://github.com/user-attachments/assets/e16e5f9c-4df7-48b7-ac47-4f8d9f09070f)
![image](https://github.com/user-attachments/assets/41cc779f-834f-4a4e-8410-f41488c62533)
![image](https://github.com/user-attachments/assets/627562de-02cf-4395-bd11-d3dc7a7dc08b)


### `Geolocation Routing Policy`

#### Overview
- **Use Case**: When you want to route traffic based on the geographic location of the user.
- **Functionality**: Routes traffic to resources based on the origin of the DNS queries.

#### Example
Users in Europe are routed to a European server, while users in North America are routed to a North American server.

### `Geoproximity Routing Policy (Traffic Flow only)`

#### Overview
- **Use Case**: Similar to geolocation, but allows more precise routing based on geographic location and a bias value to expand or shrink the geographic region.
- **Functionality**: Routes traffic based on the user's geographic location and a configurable bias.

#### Example
You can route most traffic to a nearby region but shift some percentage of traffic to another region by adjusting the bias value.

### `Multivalue Answer Routing Policy`

#### Overview
- **Use Case**: When you want to return multiple IP addresses in response to DNS queries and have health checks associated with them.
- **Functionality**: Returns multiple IP addresses (up to eight) in response to DNS queries, performing health checks on each resource.

#### Example
You have multiple web servers, and you want Route 53 to return only the IP addresses of healthy servers.

## Flow Diagram for Route 53 Routing Policies

```plaintext
Routing Policies in Route 53
|
├── Simple Routing Policy
|    └── Single Resource Response
|
├── Weighted Routing Policy
|    └── Traffic Distribution by Weights
|
├── Latency Routing Policy
|    └── Lowest Latency Response
|
├── Failover Routing Policy
|    └── Active-Passive Failover
|
├── Geolocation Routing Policy
|    └── Traffic Based on User Location
|
├── Geoproximity Routing Policy
|    └── User Location and Bias Value
|
└── Multivalue Answer Routing Policy
     └── Multiple IP Addresses with Health Checks
```
