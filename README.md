## AWS Terraform Module Development Order for Landing Zone

### 1. **Networking Module**
Start with the foundational networking components:
- **VPC**: A module for Virtual Private Cloud configuration, including CIDR blocks.
- **Subnets**: Modules for creating public and private subnets.
- **Internet Gateway (IGW)**: For outbound internet access.
- **NAT Gateway**: Enables internet access for resources in private subnets.
- **Route Tables**: Modules for defining traffic routing rules within the VPC.

### 2. **Security Module**
Set up security modules early in the development process:
- **Security Groups**: Define inbound and outbound traffic rules.
- **IAM Policies and Roles**: Manage secure access to AWS services.
- **Network ACLs**: (Optional) Additional security layer at the subnet level.

### 3. **Data Storage Module**
Modules for different types of data storage:
- **S3 Buckets**: Object storage with encryption, versioning, and access policies.
- **DynamoDB or RDS**: Modules for NoSQL or relational databases, based on needs.

### 4. **Compute Module**
Modules for running applications and services:
- **EC2 Instances**: Virtual servers, including configurations like size and AMIs.
- **ECS or EKS**: For containerized services, using Elastic Container Service or Elastic Kubernetes Service.

### 5. **Logging and Monitoring Module**
Essential for operational health and visibility:
- **CloudWatch**: For logs, metrics, monitoring, and alarms.
- **CloudTrail**: Logs and tracks user activity and API usage.

### 6. **DNS and Content Delivery Module**
For serving content to users:
- **Route 53**: DNS management and domain names.
- **CloudFront**: Content delivery network (CDN) services.

### 7. **Developer Tools Module** (Optional)
For CI/CD and source control within your landing zone:
- **CodePipeline**: Continuous integration and delivery workflows.
- **CodeCommit**: Source control repositories.

### Additional Tips:
- **Modular Design**: Ensure each module is reusable with customizable parameters.
- **Documentation**: Provide thorough documentation for each module, including inputs, outputs, and usage examples.
- **Versioning**: Use versioning for modules, especially if stored in a remote registry, to manage updates and compatibility.


### Logic

- module folder defines different resources from different aws resources
- root terragrunt.hcl defines commond resource such as provider, backend..
- terrgrunt-resource folder place the function that calls the actual parameter from items folder
- items folder keeps the actual variables of each instance