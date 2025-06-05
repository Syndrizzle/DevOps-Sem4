# Task 5: Establish a Unique IAM Policy

AWS permission management is essential to environment security, and fine-grained access control for AWS resources is made possible by *IAM (Identity and Access Management). In order to secure and restrict EC2 actions, we create a custom **IAM Policy* in this task.

In order to prevent unintentional or intentional resource loss, the goal is to allow users to *start* and *stop* EC2 instances while *explicitly denying termination* of instances. We also want to make sure that these permissions are restricted to the **us-west-2 region** and that users can *view (describe)* instances for monitoring and visibility.

The following are included in this custom policy:

- Permit: ec2:StartInstances, ec2:StopInstances  
-  Deny: ec2:TerminateInstances  
- Permit: ec2:DescribeInstances  
- Actions are only valid within the us-west-1 AWS region.

You can protect EC2 resources from unintentional termination while preserving the ability to perform necessary instance management tasks by applying this policy to particular IAM users or roles. As a best practice in cloud access management, this method strikes a balance between *security and usability*.  
#### IAM Policy for this task 
![WhatsApp Image 2025-05-31 at 01 26 54_7f6525fd](https://github.com/user-attachments/assets/074c86ad-e3ac-48d7-8981-b68502711a8e)

  