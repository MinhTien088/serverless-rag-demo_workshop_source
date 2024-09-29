---
title: "Amazon S3"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

1. Access the [AWS Console](https://console.aws.amazon.com/console), search for the **S3** service

![](/images/5.cleanup/0005-s3.png)

2. Find the S3 Bucket named `cdk-*-assets-*`, click **Empty**

![](/images/5.cleanup/0001-s3.png)

- Confirm emptying the bucket

![](/images/5.cleanup/0002-s3.png)

3. Then click **delete bucket configuration**

![](/images/5.cleanup/0003-s3.png)

- Confirm deleting the bucket

![](/images/5.cleanup/0004-s3.png)

Next, we will clean up the knowledge base in the [Amazon Bedrock](5-cleanup/5.4-knowledgebase/) service.
