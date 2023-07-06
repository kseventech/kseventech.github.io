# AWS

### Actions for making new AWS account

- Create AWS account
- Allow billing overview to IAM users
- Create IAM user admin and cli-admin
- Turn on receiving Free Tier Usage Alerts & receiving Billing Alerts
- Create billing alerts on CloudWatch
- Install AWS CLI ([guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html#cliv2-mac-install-cmd-all-users))
- Configure AWS CLI 
- Set up CloudTrail

### Root account

Root account should be used rarely, and instead, create a dedicated IAM account for accessing dashboard with admin privilieges.

### Common IAM roles 

These are the common IAM roles that every account should have.

**User name**: admin  
**Policies**: Billing, AdministratorAccess  
**Use case**: For accessing the AWS dashboard instead of using root account  

**User name**: cli-admin  
**Policies**: AdministratorAccess   
**Use case**: For managing AWS account trough CLI and Terraform  
