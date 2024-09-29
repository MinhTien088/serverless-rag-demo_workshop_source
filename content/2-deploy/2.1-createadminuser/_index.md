---
title: "Create an Admin User to deploy this stack"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1. </b> "
---

#### Section 1 - Create an IAM user with Administrator permissions (OPTIONAL: If you're already an Admin role, you may skip this step)

1. Search for the service **IAM** on the [AWS Console](https://console.aws.amazon.com/console) and go the **IAM Dashboard**

![IAM](/images/2.deploy/0001-createadminuser.png)

2. Click on **Roles** tab under **Access management** and click on **Create role**

![Create Role 1](/images/2.deploy/0002-createadminuser.png)

3. Select **AWS Account** and click **Next**

![Create Role 2](/images/2.deploy/0003-createadminuser.png)

4. Under permissions select **AdministratorAccess**

![Create Role 3](/images/2.deploy/0004-createadminuser.png)

5. Give the role a name and description, for example: `Deploy-Admin` and click on **Create role**

![Create Role 4](/images/2.deploy/0005-createadminuser.png)

6. You can now assume this role and proceed to deploy the stack. Click on **Switch role**

![Switch Role 1](/images/2.deploy/0006-createadminuser.png)

7. Provide optional display name and click on **Switch Role**

![Switch Role 2](/images/2.deploy/0007-createadminuser.png)

8. Proceed to CloudShell step
