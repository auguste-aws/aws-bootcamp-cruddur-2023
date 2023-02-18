# Week 0 — Billing and Architecture
## Required Homework/Tasks
### Creating a cost budget
The objective of this task was to create a Cost budget which monitors your costs against a specified dollar amount, and sends alerts when your user-defined thresholds are met
1. I created a monthly cost budget "My Monthly Cost Budget" with 3 alert threshold (50%, 75% and 100%). Alerts are to be sent my e-mail
2. I created a custom budget to monitor credits "Credits". When your actual cost is greater than 50% ($5.00) of my budgeted amount ($10.00), the alert threshold will be exceeded and an alert will be sent to my e-mail.
3. I created a cost budget via AWS CLI on Gitpod

Here's a screenshot of the cost budget created
![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/AWS_Budgets.png "AWS Cost Budget")

### Recreate Conceptual Diagram in Lucid Charts

I was able to recreate the following conceptual/napkin diagram in LucidChard 

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/Cruddur%20-%20Conceptual%20Diagram.png "Cruddur - Conceptual Diagram")

[LucidChart Conceptual Diagram share link](https://lucid.app/lucidchart/090c3726-1583-4ea5-a0bc-5f96ec434c01/edit?invitationId=inv_78ebfd97-5ca6-4daa-9396-d56fe2dd4774)


### Recreate Logical Diagram in Lucid Charts

I was able to recreate the following logical diagram in LucidChard 

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/Cruddur%20-%20Logical%20Diagram.png "Cruddur - Logical Diagram")

[LucidChart Logical Diagram share link](https://lucid.app/lucidchart/fa24260f-e35d-41b2-9d33-782931da5036/edit?invitationId=inv_b3c58534-3af4-4281-9065-8e3bca4ab0af)


### Security considerations for AWS IAM account

1. The first recommendation I applied was to enable MFA on root account
2. The second recommendation was to create an IAM user, add it to a group and and apply administrator permissions to the group. From now, I will use the IAM user as the management account for all the remaining tasks

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/IAM_MFA.png "Enable MFA on root user and ")

3. Create an organizational structure and roles (active accounts, standby accounts)  
4. Explore the differences between roles, groups and permissions
5. Created a Service control policy for the organization

 ![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/SCP%20_Prevent_leave_organization%20.png "SCP - Prevent Leave Organization")
 
 The code to enable this is as follows 
 ```
 {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": [
        "organizations:LeaveOrganization"
      ],
      "Resource": "*"
    }
  ]
}
```
### Install and Verify AWS CLI

First I generated access keys to enable CLI access for for the management user (IAM user)
I also enabled the gitpod button on Github by downloading and installing a browser extension here:
(https://www.gitpod.io/docs/configure/user-settings/browser-extension)

It makes it easier to launch the github code into a gitpod workspace

Installation of the AWS CLI was done as follows 

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/Install_AWS_CLI.png "Installation of AWS CLI in Gitpod terminal")
We had to setup environment variables using the access credentials we generated earlier and verified if we had access to AWS CLI by running the following command 

`aws sts get-caller-identity

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/aws-sts-get-caller-identity.png "verify identity")

### Automate installation of AWS CLI

This was done by configuring the gitpod.yml file as follows 

```
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/automate_AWS_CLI_Install.png "Automate installation of AWS CLI")


### Creating a cost budget via AWS CLI

I also created a cost budget via CLI using three files that were provided by Andrew Brown 

![alt text](https://github.com/auguste-aws/aws-bootcamp-cruddur-2023/blob/week-0/_docs/assets/aws-sts-get-caller-identity.png "Create Cost Budget via AWS CLI")




