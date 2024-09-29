---
title: "Deploy the RAG based Solution"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2. </b> "
---

#### Section 2 - Deploy this RAG based Solution (The below commands should be executed in the region of deployment)

1. Switch to Admin role. Search for CloudShell service on the AWS Console and follow the steps below to clone the github repository

![CloudShell](/images/2.deploy/0001-deployragbasedsolution.png)

2. Git clone the serverless-rag-demo repository from aws-samples

```bash
git clone https://github.com/aws-samples/serverless-rag-demo.git
```

![git clone https://github.com/aws-samples/serverless-rag-demo.git](/images/2.deploy/0002-deployragbasedsolution.png)

3. Go to the directory where we have the downloaded files.

```bash
cd serverless-rag-demo
```

![cd serverless-rag-demo](/images/2.deploy/0003-deployragbasedsolution.png)

4. Fire the bash script that creates the RAG based solution. Pass the environment and region for deployment. environment can be `dev`, `qa`, `sandbox` by running different commands like `sh creator.sh dev`, `sh creator.sh qa` or `sh creator.sh sandbox` (default is *dev*). (Look at [Prerequisites](1-prerequisites/) to deploy to the correct region.)

```bash
sh creator.sh
```

![sh creator.sh](/images/2.deploy/0004-deployragbasedsolution.png)

5. Type `1` to select the **N.Virginia** region

![Choose Region](/images/2.deploy/0005-deployragbasedsolution.png)

6. Type `1` to select the **Deploy Amazon OpenSearch Serverless vertor engine for RAG** option. Press **Enter** to proceed with deployment of the stack or **Ctrl + C** to exit

![Choose Region](/images/2.deploy/0006-deployragbasedsolution.png)

7. The UI is hosted on AppRunner the link to AppRunner could be found in CloudShell once the script execution is complete, or you could also go to the [AppRunner service](https://console.aws.amazon.com/apprunner) on the AWS Console and obtain the https url. The UI is authenticated through Amazon Cognito hence the very first time you would have to sign-up and then sign-in to login to the application

![in CloudShell](/images/2.deploy/0007-deployragbasedsolution-2.png)

![in App Runner UI](/images/2.deploy/0007-deployragbasedsolution-1.png)

8. On Amazon Bedrock page enable access to the below models

![Amazon Bedrock access models](/images/2.deploy/0008-deployragbasedsolution.png)
