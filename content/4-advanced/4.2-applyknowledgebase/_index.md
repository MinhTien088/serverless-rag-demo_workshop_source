---
title: "Apply the knowledge base to the Serverless RAG demo"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

1. Get the information about **Embeddings model**, **Collection ARN**, and **Vector index name** used by the existing knowledge base on Bedrock

![Collection-ARN](/images/4.advanced/0012-createknowledgebase.png)

2. Access the [AWS Console](https://console.aws.amazon.com/console), search for the **Amazon OpenSearch** service

![](/images/4.advanced/0001-applyknowledgebase.png)

3. Access Amazon OpenSearch Serverless and search by ARN to get the OpenSearch Endpoint

![](/images/4.advanced/0002-applyknowledgebase.png)

![OSS-Endpoint](/images/4.advanced/0003-applyknowledgebase.png)

4. Find the ID of the Embedding model used by Bedrock KB from [here](https://docs.aws.amazon.com/bedrock/latest/userguide/model-ids.html)

![](/images/4.advanced/0013-applyknowledgebase.png)

5. Access the [AWS Console](https://console.aws.amazon.com/console), search for the **Lambda** service

![](/images/4.advanced/0014-applyknowledgebase.png)

6. Find the lambda function `bedrock_rag_query_`, then proceed with the following setup steps

![](/images/4.advanced/0015-applyknowledgebase.png)

- Select the **Configuration** tab
- Choose **Environment variables**
- Click **Edit**

![](/images/4.advanced/0011-applyknowledgebase.png)

Set up as follows:
   
   a. **IS_BEDROCK_KB** = `yes`  

   b. **OPENSEARCH_VECTOR_ENDPOINT** = <<Amazon OpenSearch Serverless Endpoint of the existing Bedrock KB>> (not including **https://**)

   c. **EMBED_MODEL_ID** = <<Embedding Model ID used by the existing Bedrock KB>>

   d. **VECTOR_INDEX_NAME** = <<VECTOR_INDEX used by the existing Bedrock KB>>

   ![Lambda-Config](/images/4.advanced/0012-applyknowledgebase.png)

- Then click **Save**
   
7. Get the ARN of the Lambda role

- Select the **Configuration** tab
- Choose **Permissions**
- Click on the link at Role name

![Lambda-Config](/images/4.advanced/0006-applyknowledgebase.png)

- In the role interface, note down the ARN of that role

![Lambda-Config](/images/4.advanced/0007-applyknowledgebase.png)

8. Go back to the Amazon OpenSearch tab from step 3. In the **Data access** section, access the **Associated policy** link, then click **Edit**

![Lambda-Config](/images/4.advanced/0004-applyknowledgebase.png)

![Lambda-Config](/images/4.advanced/0005-applyknowledgebase.png)

9. Select **Add principals**, click **IAM users and roles**

![Lambda-Config](/images/4.advanced/0008-applyknowledgebase.png)

- Provide the ARN of the role noted in step 7, then click **Save**

![Lambda-Config](/images/4.advanced/0009-applyknowledgebase.png)

- Complete

![Lambda-Config](/images/4.advanced/0010-applyknowledgebase.png)

10. Now try Document Chat on the user interface, it will query from the Amazon Bedrock knowledge base.

![Lambda-Config](/images/4.advanced/0016-applyknowledgebase.jpg)
