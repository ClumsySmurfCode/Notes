# Connection Draining

## Overview
Connection Draining (also known as Deregistration Delay) is a feature in AWS Elastic Load Balancing that ensures that existing connections are allowed to complete before a target is deregistered or becomes unhealthy. This helps in maintaining a seamless user experience by preventing interruptions during maintenance or scaling activities.

## Key Features
- **Graceful Deregistration**: Allows existing connections to continue while new connections are not sent to the target.
- **Timeout Period**: Configurable timeout period to specify how long the load balancer should wait for connections to complete.
- **Prevents Interruption**: Ensures that in-flight requests are completed, minimizing disruptions for users.

## How Connection Draining Works
1. **Target Becomes Unavailable**: A target (e.g., EC2 instance) is marked for removal or becomes unhealthy.
2. **Connection Draining Starts**: The load balancer stops sending new requests to the target.
3. **Existing Connections Complete**: Ongoing requests continue to be served by the target until they complete or the timeout period expires.
4. **Target Deregistered**: After the timeout period, the target is deregistered, and any remaining connections are closed.

## Use Cases
- **Maintenance**: Graceful handling of user sessions during maintenance windows.
- **Scaling**: Smooth transition when scaling in or out by ensuring active sessions are not interrupted.
- **Instance Termination**: Safe deregistration of instances scheduled for termination.

## Configuring Connection Draining
Connection Draining can be enabled and configured via the AWS Management Console, AWS CLI, or AWS SDKs. The key parameter to configure is the **timeout period**, which can be set between 1 and 3600 seconds.

## Flow Diagram for Connection Draining

```plaintext
+------------------------+
| Target (e.g., EC2)     |
| marked for removal     |
+-----------+------------+
            |
            V
+-----------+------------+
| Load Balancer stops    |
| sending new requests   |
+-----------+------------+
            |
            V
+-----------+------------+
| Existing connections   |
| continue to be served  |
+-----------+------------+
            |
            V
+-----------+------------+
| Connections complete or|
| timeout period expires |
+-----------+------------+
            |
            V
+-----------+------------+
| Target deregistered    |
+------------------------+
```

## Description of the Flow Diagram

1. **Target Marked for Removal**: The target (e.g., EC2 instance) is marked for removal or becomes unhealthy.
2. **Load Balancer Stops Sending New Requests**: The load balancer stops routing new requests to the target.
3. **Existing Connections Continue**: Ongoing connections are allowed to complete, serving active requests.
4. **Connections Complete or Timeout**: Connections are allowed to complete until the timeout period expires.
5. **Target Deregistered**: After the timeout period, the target is fully deregistered, and any remaining connections are closed.
