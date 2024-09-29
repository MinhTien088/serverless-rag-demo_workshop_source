---
title: "CloudFormation"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

1. Access the [AWS Console](https://console.aws.amazon.com/console), search for the **CloudFormation** service

![](/images/5.cleanup/0001-cloudformation.png)

2. In the sidebar, select **Stack**, choose the stack you want to delete, then click **Delete**

![](/images/5.cleanup/0002-cloudformation.png)

3. Continue by clicking **Delete** to confirm the stack deletion

![](/images/5.cleanup/0003-cloudformation.png)

{{% notice info %}}
Based on the steps above, delete the following stacks in order:
{{% /notice %}}

> 1. AppRunnerHostingdevStack
> 2. ApiGwLlmsLambdadevStack
> 3. LlmsWithServerlessRagdevStack
> 4. CDKToolkit

{{% notice warning %}}
**Delete them in order**, don't worry about the Nested stacks (as the Nested stacks will be automatically deleted along with the main stack)
{{% /notice %}}

Next, we will clean up the resources for the [Amazon Cognito](5-cleanup/5.2-cognito/) service.
