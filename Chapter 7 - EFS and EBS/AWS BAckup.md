
# AWS Backup

- backup allows you to consolidate backups from multiple services
  - ec2
  - ebs
  - efs
  - amazon fsx for lustre
  - amazon fsx for windows file server
  - aws storage gateway
- it can include other services such as database technologies like RDS and DynamoDB

- Backups can be used with organizations
- It gives you centralized control across all AWS services, in multiple AWS accounts across the entive AWS organization.

## Benefits
- central management for different services
- automation
  - you can create automated backup schedules
  - retention policies
  - create lifecycle policies
  - allow to expire unnecessary backupts after a period of time
- imporived compliance
  - backup policies can be enforced
  

## Gives you

**Consolidation**: allows to centralize backup for multiple servies

**Organizations**: can be used accross different accounts
**Benefits**: centralized control, letting you automate your backups and define lifecycle policies for your data. You get better compliance, as you can enforce your backup policies, ensure your backups are encrypted and audit them once complete.