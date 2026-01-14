# AWS Cloud Security – Detailed Verification Guide

This document provides **step-by-step guidance** for validating each security control listed in `checklist.md`.  
It is designed for **beginners to intermediate AWS users** and focuses on **AWS Management Console verification**.

---

## Identity & Access Management (IAM)

### 1. Root account MFA enabled
**How to check:**
1. Log in to the AWS Management Console
2. Click your account name (top right) → *Security Credentials*
3. Under *Multi-factor authentication*, confirm MFA is enabled

---

### 2. IAM user MFA enforced
**How to check:**
1. Go to **IAM → Users**
2. Select each user
3. Verify MFA status under *Security credentials*

---

### 3. No shared long-term credentials
**How to check:**
1. Review IAM users
2. Confirm each user represents a single individual
3. Ensure no shared access keys are used across teams

---

### 4. Cross-account access requires MFA
**How to check:**
1. Go to **IAM → Roles**
2. Review trust policies
3. Confirm MFA condition (`aws:MultiFactorAuthPresent`) exists

---

### 5. Strong account password policy
**How to check:**
1. IAM → Account settings
2. Verify:
   - Minimum length
   - Complexity
   - Reuse prevention

---

### 6. Password rotation enabled
**How to check:**
- IAM → Account settings → Password policy
- Confirm password expiration ≤ 90 days

---

### 7. No overly permissive IAM policies
**How to check:**
1. IAM → Policies
2. Review for:
   - `*:*`
   - `AdministratorAccess`
3. Confirm least privilege

---

### 8. IAM roles follow least privilege
**How to check:**
- IAM → Roles → Permissions
- Ensure permissions match workload needs only

---

### 9. IAM Access Analyzer enabled
**How to check:**
- IAM → Access Analyzer
- Confirm analyzer exists and is active

---

### 10. No root access keys exist
**How to check:**
- IAM → Security credentials
- Confirm no access keys under root account

---

### 11. Credentials rotated regularly
**How to check:**
- IAM → Users → Access keys
- Review key age

---

### 12. Strong TLS certificates
**How to check:**
- ACM → Certificates
- Confirm RSA 2048+ or ECDSA usage

---

### 13. No deprecated certificates
**How to check:**
- ACM → Certificates
- Ensure none use weak algorithms

---

### 14. Security questions configured
**How to check:**
- Account → Security credentials
- Verify recovery options

---

### 15. Security contact information set
**How to check:**
- AWS Console → Account → Alternate contacts

---

### 16. AWS Organizations in use
**How to check:**
- AWS Organizations service
- Confirm organization exists

---

### 17. Unused IAM identities removed
**How to check:**
- IAM → Users / Roles
- Remove unused or inactive identities

---

## Compute & Load Balancing (EC2 / ELB)

### 18. No unrestricted security group rules
**How to check:**
- EC2 → Security Groups
- Review inbound rules for `0.0.0.0/0`

---

### 19. EC2 termination protection enabled
**How to check:**
- EC2 → Instance → Actions → Instance settings

---

### 20. No public AMIs in use
**How to check:**
- EC2 → AMIs
- Confirm source is private or trusted

---

### 21. Approved AMIs only
**How to check:**
- Validate AMI IDs against approved baseline

---

### 22. EBS snapshots not public
**How to check:**
- EC2 → Snapshots
- Permissions → Ensure private

---

### 23. EBS encryption enabled
**How to check:**
- EC2 → Volumes → Encryption status

---

### 24. EBS uses CMK
**How to check:**
- Volume → Encryption key
- Confirm customer-managed KMS key

---

### 25. ALB strong TLS policies
**How to check:**
- EC2 → Load Balancers → Listeners

---

### 26. WAF attached to ALB
**How to check:**
- WAF & Shield → Web ACLs

---

### 27. HTTPS-only listeners
**How to check:**
- Load balancer → Listeners → HTTPS only

---

### 28. Load balancer deletion protection
**How to check:**
- Load balancer attributes

---

### 29. ELB access logging enabled
**How to check:**
- Load balancer → Attributes → Access logs

---

## Storage (S3)

### 30. No public buckets
**How to check:**
- S3 → Bucket → Permissions
- Block Public Access enabled

---

### 31. Restricted bucket policies
**How to check:**
- S3 → Bucket policy
- Review cross-account access

---

### 32. Server-side encryption enforced
**How to check:**
- S3 → Properties → Default encryption

---

### 33. CMK used for S3 encryption
**How to check:**
- Encryption settings → KMS CMK

---

### 34. Versioning enabled
**How to check:**
- Bucket → Properties → Versioning

---

### 35. MFA Delete enabled
**How to check:**
- S3 versioning configuration

---

### 36. Access logging enabled
**How to check:**
- Bucket → Properties → Logging

---

### 37. HTTPS enforced
**How to check:**
- Bucket policy denies non-SSL access

---

## Networking (VPC / Route 53)

### 38. VPC Flow Logs enabled
**How to check:**
- VPC → Flow Logs

---

### 39. DNSSEC enabled
**How to check:**
- Route 53 → Hosted zones → DNSSEC

---

### 40. Domain transfer lock enabled
**How to check:**
- Route 53 → Domains → Settings

---

### 41. SPF record configured
**How to check:**
- Route 53 → DNS records

---

### 42. Expired domains restored
**How to check:**
- Route 53 → Domains → Status

---

### 43. Domains renewed early
**How to check:**
- Expiration date review

---

## Logging & Monitoring

### 44. CloudTrail enabled
**How to check:**
- CloudTrail → Trails

---

### 45. CloudTrail encrypted
**How to check:**
- Trail → Encryption settings

---

### 46. Log integrity validation
**How to check:**
- CloudTrail → Trail settings

---

### 47. CloudTrail → CloudWatch
**How to check:**
- Trail → CloudWatch Logs integration

---

### 48. AWS Config enabled
**How to check:**
- AWS Config → Settings

---

### 49. Config rules evaluated
**How to check:**
- AWS Config → Rules

---

### 50. Non-compliance reviewed
**How to check:**
- AWS Config → Dashboard

---

### 51. GuardDuty enabled
**How to check:**
- GuardDuty → Accounts

---

### 52. GuardDuty findings reviewed
**How to check:**
- GuardDuty → Findings

---

## Databases

### 53. RDS not public
**How to check:**
- RDS → Connectivity → Public access

---

### 54. Automated backups enabled
**How to check:**
- RDS → Backup settings

---

### 55. Storage encryption enabled
**How to check:**
- RDS → Encryption

---

### 56. CMK used for RDS
**How to check:**
- RDS → KMS key

---

### 57. Snapshots encrypted
**How to check:**
- RDS → Snapshots

---

### 58. Logging enabled
**How to check:**
- RDS → Logs & events

---

### 59. IAM authentication enabled
**How to check:**
- RDS → Authentication settings

---

### 60. Auto minor upgrades enabled
**How to check:**
- RDS → Maintenance

---

### 61. Engines up to date
**How to check:**
- Engine version review

---

### 62. TLS enforced
**How to check:**
- Parameter groups

---

### 63. Backup retention compliant
**How to check:**
- Backup retention period

---

### 64. Certificates valid
**How to check:**
- RDS certificate details

---

### 65. Multi-AZ enabled
**How to check:**
- RDS → Availability

---

### 66. DynamoDB backups enabled
**How to check:**
- DynamoDB → Backups

---

### 67. DynamoDB encrypted
**How to check:**
- Table → Encryption

---

## Messaging & Queues

### 68. SNS access restricted
**How to check:**
- SNS → Access policy

---

### 69. SNS not public
**How to check:**
- Subscription permissions

---

### 70. SNS encryption enabled
**How to check:**
- Topic → Encryption

---

### 71. SNS CMK used
**How to check:**
- Encryption key settings

---

### 72. SQS encryption enabled
**How to check:**
- Queue → Encryption

---

### 73. SQS CMK used
**How to check:**
- KMS key selection

---

### 74. SQS not public
**How to check:**
- Queue policy

---

### 75. Cross-account SQS restricted
**How to check:**
- Policy review

---

## Key Management

### 76. CMK rotation enabled
**How to check:**
- KMS → Key rotation

---

### 77. KMS keys not public
**How to check:**
- Key policy review

---

### 78. Cross-account KMS restricted
**How to check:**
- Key policy

---

## Serverless (Lambda)

### 79. Code signing enabled
**How to check:**
- Lambda → Code signing

---

### 80. Supported runtimes used
**How to check:**
- Lambda → Runtime version

---

### 81. Cross-account invoke restricted
**How to check:**
- Function policy

---

### 82. Lambda not public
**How to check:**
- Resource-based policies

---

### 83. Env vars encrypted
**How to check:**
- Lambda → Environment variables

---

## Containers (EKS)

### 84. Secrets encryption enabled
**How to check:**
- EKS → Cluster → Encryption

---

### 85. Control plane logging enabled
**How to check:**
- EKS → Logging

---

### 86. Kubernetes version current
**How to check:**
- Cluster version review

---

### 87. API endpoint private
**How to check:**
- EKS → Endpoint access

---

## Backup & Recovery

### 88. Backup vault deletion protection
**How to check:**
- AWS Backup → Vault settings

---

## Analytics & Caching

### 89. Redshift not public
**How to check:**
- Redshift → Network settings

---

### 90. ElastiCache supported versions
**How to check:**
- Engine version review

---

### 91. ElastiCache encrypted
**How to check:**
- Encryption settings

---

## Content Delivery

### 92. CloudFront logging enabled
**How to check:**
- CloudFront → Distribution → Logging

---

### 93. WAF attached to CloudFront
**How to check:**
- WAF → Web ACL associations

---

### 94. Legacy TLS disabled
**How to check:**
- CloudFront → Security policy
