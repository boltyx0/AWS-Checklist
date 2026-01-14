## Identity & Access Management (IAM)

- [ ] Root account login is protected with multi-factor authentication (MFA)
- [ ] IAM users are required to use MFA for console access
- [ ] Long-term credentials are not shared between users
- [ ] Cross-account access enforces MFA and explicit trust relationships
- [ ] Account-wide password policies enforce strong complexity requirements
- [ ] Password rotation is enforced (90 days or less)
- [ ] IAM policies avoid wildcard permissions and excessive actions
- [ ] IAM roles are designed using least-privilege principles
- [ ] IAM Access Analyzer is enabled to detect unintended resource sharing
- [ ] Root account access keys do not exist
- [ ] SSH keys and API credentials are rotated on a regular basis
- [ ] TLS certificates use modern cryptographic standards (RSA 2048+ or ECDSA)
- [ ] Deprecated or legacy certificates are not in use
- [ ] Security questions are configured for account recovery
- [ ] Security contact information is configured and up to date
- [ ] AWS Organizations is used for centralized identity management
- [ ] Unused IAM users, roles, and credentials are removed regularly

---

## Compute & Load Balancing (EC2 / ELB / AMIs)

- [ ] Security groups do not allow unrestricted inbound access (0.0.0.0/0)
- [ ] EC2 termination protection is enabled where applicable
- [ ] Publicly shared AMIs are not used
- [ ] Only approved and hardened AMIs are deployed
- [ ] EBS snapshots are not publicly accessible
- [ ] EBS volumes are encrypted at rest
- [ ] EBS encryption uses customer-managed KMS keys
- [ ] Application Load Balancers enforce strong TLS security policies
- [ ] Load balancers are integrated with AWS Web Application Firewall (WAF)
- [ ] Load balancers enforce HTTPS-only listeners
- [ ] Deletion protection is enabled for production load balancers
- [ ] Access logging is enabled for Elastic Load Balancers

---

## Storage (S3)

- [ ] S3 buckets are not publicly accessible
- [ ] Bucket policies restrict unauthorized cross-account access
- [ ] Server-side encryption is enforced for all objects
- [ ] Encryption uses customer-managed KMS keys
- [ ] Object versioning is enabled
- [ ] MFA Delete is enabled for sensitive buckets
- [ ] S3 access logging is enabled
- [ ] Secure transport (HTTPS) is enforced for all access

---

## Networking (VPC / Route 53)

- [ ] VPC Flow Logs are enabled in all regions
- [ ] DNSSEC signing is enabled for Route 53 hosted zones
- [ ] Domain transfer locks are enabled
- [ ] SPF records are configured to prevent email spoofing
- [ ] Expired Route 53 domains are restored
- [ ] Domains nearing expiration are renewed proactively

---

## Logging, Monitoring & Detection

### CloudTrail

- [ ] CloudTrail is enabled in all regions
- [ ] CloudTrail logs are encrypted using KMS
- [ ] Log file integrity validation is enabled
- [ ] CloudTrail events are forwarded to CloudWatch Logs

### AWS Config

- [ ] AWS Config is enabled
- [ ] Config rules are actively evaluated
- [ ] Non-compliant resources are reviewed and remediated

### GuardDuty

- [ ] GuardDuty is enabled across all accounts and regions
- [ ] GuardDuty findings are reviewed and validated

---

## Databases (RDS / DynamoDB)

### RDS

- [ ] RDS instances are not publicly accessible
- [ ] Automated backups are enabled
- [ ] Storage encryption is enabled
- [ ] Encryption uses customer-managed KMS keys
- [ ] Database snapshots are encrypted
- [ ] Performance and audit logging is enabled
- [ ] IAM database authentication is enabled where supported
- [ ] Automatic minor version upgrades are enabled
- [ ] Database engines are kept up to date
- [ ] Secure transport (TLS) is enforced
- [ ] Backup retention meets compliance requirements
- [ ] SSL/TLS certificates are valid and current
- [ ] Multi-AZ deployments are enabled for production databases

### DynamoDB

- [ ] Continuous backups are enabled
- [ ] Tables use KMS-based encryption

---

## Messaging & Queues (SNS / SQS)

### SNS

- [ ] SNS topics do not allow unrestricted access
- [ ] SNS topics are not publicly exposed
- [ ] Server-side encryption is enabled
- [ ] Encryption uses customer-managed KMS keys

### SQS

- [ ] SQS queues enforce server-side encryption
- [ ] Customer-managed KMS keys are used for encryption
- [ ] Queues are not publicly accessible
- [ ] Cross-account access is explicitly restricted

---

## Key Management Service (KMS)

- [ ] Customer-managed keys have automatic rotation enabled
- [ ] KMS keys are not publicly accessible
- [ ] Cross-account key usage is tightly restricted

---

## Serverless (Lambda)

- [ ] Lambda functions enforce code signing
- [ ] Functions use supported and up-to-date runtimes
- [ ] Cross-account invocation is restricted
- [ ] Lambda functions are not publicly exposed
- [ ] Environment variables are encrypted using KMS

---

## Containers & Orchestration (EKS)

- [ ] Secrets encryption is enabled
- [ ] Control plane logging is enabled
- [ ] Kubernetes cluster versions are kept up to date
- [ ] Cluster API endpoints are not publicly accessible

---

## Backup & Recovery

- [ ] AWS Backup vaults are protected from accidental deletion

---

## Analytics & Caching

### Redshift

- [ ] Redshift clusters are not publicly accessible

### ElastiCache

- [ ] Supported engine versions are used
- [ ] Encryption is enabled at rest and in transit

---

## Content Delivery & Edge Security (CloudFront)

- [ ] Access logging is enabled
- [ ] Web Application Firewall (WAF) is attached
- [ ] Legacy TLS versions (1.0 and 1.1) are disabled
