### AWS EC2 Instance Metadata

EC2 instance metadata is a service provided by AWS that allows instances to retrieve data about themselves. This metadata is accessible from within the instance and includes information such as instance ID, instance type, security groups, and more. Here’s an overview and how it can be used:

#### Accessing Instance Metadata

Instance metadata can be accessed using HTTP requests to a special IP address `http://169.254.169.254`. Here is an example of how to retrieve instance metadata:

```sh
curl http://169.254.169.254/latest/meta-data/
```

This command will return a list of available metadata categories.

#### Metadata Categories

- **ami-id**: The ID of the AMI used to launch the instance.
- **instance-id**: The ID of the instance.
- **instance-type**: The type of the instance (e.g., t2.micro).
- **hostname**: The private DNS hostname of the instance.
- **local-ipv4**: The private IPv4 address of the instance.
- **public-ipv4**: The public IPv4 address of the instance (if applicable).
- **security-groups**: The names of the security groups applied to the instance.
- **public-hostname**: The public DNS hostname of the instance (if applicable).

#### Usage Examples

- **Retrieve Instance ID**:
  ```sh
  curl http://169.254.169.254/latest/meta-data/instance-id
  ```
  
- **Retrieve AMI ID**:
  ```sh
  curl http://169.254.169.254/latest/meta-data/ami-id
  ```

- **Retrieve Security Groups**:
  ```sh
  curl http://169.254.169.254/latest/meta-data/security-groups
  ```

#### IAM Role Credentials

EC2 instance metadata also provides temporary security credentials for IAM roles assigned to the instance. These credentials can be used to securely access AWS services. The endpoint to retrieve these credentials is:

```sh
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/{role-name}
```

#### Metadata vs. User Data

- **Metadata**: Data about the instance that AWS provides. It is static and cannot be modified by the user.
- **User Data**: Data that can be passed to the instance at launch time, typically used to run initialization scripts or configuration commands. User data is accessed via:

  ```sh
  curl http://169.254.169.254/latest/user-data/
  ```
