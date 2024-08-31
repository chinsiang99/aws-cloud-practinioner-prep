# Security and Compliance
- 30% of the exam
- AWS shared responsibility model
- AWS Cloud security, governance, and compliance concepts
- AWS access management capabilities
- Identify components and resources for security

# Security in the Cloud

## IT Infrastructure: In the Past
- Server rooms secured with key cards
- Off-site data centers
- Lots of security devices and people
- Difficult to access

## IT Infrastructure: Present-Day AWS Cloud
- Global network of data centers built with security in mind
- Safeguards to protect customer privacy
- Dozens of compliance programs to help meet industry compliance requirements for data security
- High security standards without need for your own data centers
- Scale your business quickly

## Shared Responsibility Model (Your responsibility vs AWS responsibility)
- Security of cloud computing infrastructures and data is a **shared responsibility** between the customer and AWS
- AWS is responsibility of the security of the Cloud
- We or customers are responsibility with the security in the Cloud

## Security in the Cloud
- Identity and access management (IAM)
- Detective controls
- Infrastructure protection
- Data protection
- Incident response

# Access Management

## Providing Access in AWS

### Security Groups vs. NACLs

| Security Groups | NACLs (Network Access Control Lists) |
|-----------------|-------|
| Protect at instance level | Protect at subnet level |
| Stateful: traffic allowed in is allowed out ("remembers") | Stateless: in and out traffic need to be defined separately ("forgets") |
| No explicit deny | Explicit deny (meaning that is more important than other rules) |
| All inbound traffic blocked and outbound traffic allowed by default | All inbound and outbound traffic allowed by default |


## Identity Acess management (IAM)
- Manage access to services and resources in the AWS Cloud
- Manage users and groups
- Can provide access to users or other AWS services
- Permissions are global; any access setting will be true all across regions
- Follow principle of least privilege

### Method 1 : Manage Users
- Create users in IAM and assign them security credentials
- Users can have very precise permission sets
- Users can access AWS through AWS management console
- You can provide programmatic access to data / resources
- Programmatic access: applications directly access resources instead of humans doing the same activity

### Method 2 : Manage IAM Roles
- Create roles to manage permissions and what those roles can do
- An entity assumes a role to obtain temporary security credentials to make API calls to your resources
- Used to provide a user from another AWS account with access to your AWS account

### Method 3 : Manage federated Users
- enable identity federation: allow existing identities in your enterprise to access AWS without having to create an IAM user for each identity

### Benefits of IAM
- Enhanced security
- granular Control
- Ability to provide temporary credentials
- Flexible Security credential management 
- Federated access
- Seamless integration across various AWS services

## Principle of Least Privilege
- Who can access what?
- Every role has a set of access permissions necessary to effectively completes its jobs, and the individual in the role should have no more and no less than the optimal level of access

## Keeping accounts secured

### Security Credentials
- Password Policy: password requirement, rotation of passwords
- Access key: to make programmatic calls to AWS; should be used temporarily

### Multifactor Authentication (MFA)
- Aka two-factor authentication (2FA)
- User presents at least two pieces of evidence (factors) that verify they should access the said account

### AWS Secrets Manager
- Saves all your "secrets" for you
- Secrets: passwords, credentials, tokens, access keys etc
- Integrates with key AWS services

# Security Services

## AWS Systems Manager
- Centralized control tower to manage AWS resources in multicloud and hybrid environments
- Visualize and operate on multiple AWS services from one place
- Create logical groups of resources, then select a resource group to view metrics and take action
- Helps IT admins make sure that IT infrastructure is running smoothly and alerts them when resources are not meeting internal compliance policies

## AWS WAF (web application firewall)
- Protects web apps running on the AWS Cloud from common web exploits
- Firewall services for web applications
- Protects web app against exploits that could compromise security or avaialbility
- Protects apps from exploits that could force them to consume excessive resources
- It imporves web traffic visibility
- Provides cost-effective web app protection
- Increased security and protetcion against web attacks
- easy to deploy and maintain
- It can be deployed on Amazon CloudFront, Application Load Balancer, Amazon API Gateway, or AWS AppSync
- It can be deployed on Amazon CloudFront, Application Load Balancer, Amazon API Gateway, or AWS AppSync

## AWS Shield (partially free)
- Provides detection and automatic mitigations
- Minimizes effects of DDoS atatcks on your apps
- Helps minimize application downtime and latency when an attack happens

### AWS Shield : Standard
- Automatically enabled
- Free
- Protects web applications against a majority of common DDoS attacks

### AWS Shield : Advanced
- Continuous, 24/7 access to AWS DDoS response team
- Near real-time visibility into events
- Integrates with AWS WAF
- Provides high-level protections, network and transport layer protections, and automated application traffic monitoring
- Financial protection against DDoS-related spikes in charges for EC2, elastic load balancers, CloudFront, and Route 53
- Available globally on CloudFront and Route 53 edge locations
- Your web application can be hosted anywhere in the world and still be protected by AWS Shield

## Amazon Inspector
- Automated security assessment service for applications
- Automatically assesses for exposure, vulnerabilities, and deviation from best practices
- Genrates detailed reports to help check for vulnerabilities
- Security teams can get reports validating that tests were performed
- Reduce risks of introducing security issues during deployment and development
- Overall, it inspects your applications to find security issues

## AWS Trusted Advisor (partially free)
- Guides provisioning of resources to follow AWS best practices
- Scans your infrastructure and advises you on how it is or is not following AWS best practices
- Based on five categories: cost optimization, performance, security, fault tolerance, service limits
- Provides action recommendations to meet best practices

### Seven Core Trusted Advisor Checks
1. S3 bucket permissions
2. Security groups - specific ports unrestricted
3. IAM use
4. MFA on root account
5. Elastic Block Store (EBS) public snapshots
6. Relational Database Service (RDS) public snapshots
7. Service limits

### Full Trusted Advisor Checks (paid)
- More types of checks on top of core checks
- Notifications through weekly updates
- Set up automated actions in response to alerts using CloudWatch
- Programmatic access to scan results via AWS Support API

## When to Use Amazon Inspector vs. AWS Trusted Advisor:
Use Amazon Inspector when:

You need to perform detailed security assessments of your EC2 instances or container images.
You want to identify and remediate specific security vulnerabilities in your workloads.
You require continuous security monitoring to meet compliance requirements.
Use AWS Trusted Advisor when:

You want to **optimize your AWS environment** in terms of cost, performance, security, and fault tolerance.
You need broad recommendations across various aspects of your AWS infrastructure, including cost savings and best practices.
You are managing multiple AWS resources and want to ensure that your environment is well-architected and adheres to AWS best practices.
Summary:
Amazon Inspector is focused on security vulnerability assessments for your workloads.
AWS Trusted Advisor provides a broader range of recommendations across cost, performance, security, and more.