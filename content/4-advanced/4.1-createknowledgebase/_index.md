---
title: "Create an Amazon Bedrock Knowledge base"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

1. Access [AWS Console](https://console.aws.amazon.com/console), search for the **Amazon Bedrock** service

![](/images/4.advanced/0014-createknowledgebase.png)

2. In the sidebar, select **Knowledge bases**, then click **Create knowledge base**

![](/images/4.advanced/0001-createknowledgebase.png)

3. Name your knowledge base (optional)

![](/images/4.advanced/0002-createknowledgebase.png)

4. In the **Choose data source** section, select **Web Crawler**, then click **Next**

![](/images/4.advanced/0003-createknowledgebase.png)

5. Name your data source (optional). In the **Source URLs** section, enter `https://gohugo.io/documentation/`, then click **Next**

![](/images/4.advanced/0004-createknowledgebase.png)

6. In the **Embeddings model** section, select **Embed Multilingual v3 - By Cohere**, then click **Next**

![](/images/4.advanced/0005-createknowledgebase.png)

7. Review the settings you've configured, then click **Create knowledge base**

![](/images/4.advanced/0006-createknowledgebase.png)

8. After the knowledge base is created, click **Go to data sources**

![](/images/4.advanced/0007-createknowledgebase.png)

9. Select the existing Data source, then click **Sync**

![](/images/4.advanced/0008-createknowledgebase.png)

The data synchronization process will take some time, depending on the provided data source.

10. After completing the data synchronization process, we will test the knowledge base.

- Click **Select model**

![](/images/4.advanced/0009-createknowledgebase.png)

- Choose **Anthropic** as the **Model providers**
- Select the **Claude 3.5 Sonnet** model
- Click **Apply**

![](/images/4.advanced/0010-createknowledgebase.png)

- Enter a question and check the answer

![](/images/4.advanced/0011-createknowledgebase.png)

11. The process of creating the knowledge base is complete. We will note down the information about the **Embeddings model**, **Collection ARN**, and **Vector index name**

![](/images/4.advanced/0012-createknowledgebase.png)
