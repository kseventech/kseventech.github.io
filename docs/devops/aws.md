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

### K7 Tech Root account

**Email**: k7tech.ops@gmail.com  
**Name**: kseventech  
**Account ID**: 053066921341

### IAM 

**User name**: admin  
**Access**: AWS Management Console access  
**Policies**: Billing, AdministratorAccess  
**Use case**: For accessing the AWS dashboard instead of using root account  

**User name**: cli-admin  
**Access**: Programmatic access  
**Policies**: AdministratorAccess   
**Use case**: For managing AWS account trough CLI and Terraform  

**User name**: ecr-user  
**Access**: Programmatic access  
**Policies**: AmazonEC2ContainerRegistryPowerUser   
**Use case**: For uploading docker images to Amazon container registry ECR

