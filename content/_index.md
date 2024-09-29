---
title: "Serverless RAG demo"
date: "`r Sys.Date()`" 
weight: 1 
chapter: false
---

# Scalable RAG solutions/Agentic Workflows with Amazon Bedrock and Amazon Opensearch serverless service

### Overview

Widespread AI adoption is being driven by generative AI models that can generate human-like content. However, these foundation models are trained on general data making it less effective for domain specific tasks. There lies the importance of Retrieval Augmented Generation (RAG). RAG allows augmenting prompts with relevant external data for better domain-specific outputs. With RAG, documents and queries are converted to embeddings, compared to find relevant context, and that context is appended to the original prompt before being passed to the LLM. Knowledge libraries can be updated asynchronously to provide the most relevant external data for augmenting prompts.

[Amazon OpenSearch Serverless (AOSS) offers vector engine to store embeddings for faster similarity searches](https://aws.amazon.com/blogs/big-data/introducing-the-vector-engine-for-amazon-opensearch-serverless-now-in-preview/). The vector engine provides a simple, scalable, and high-performing similarity search capability in Amazon OpenSearch Serverless that makes it easy for you to build generative artificial intelligence (AI) applications without having to manage the underlying vector database infrastructure.

{{% notice note %}}
This workshop offers a production ready easily deployable Generative AI solution with the below features:
>   1. Document chat
>   2. Multi-Agent collaboration
>   3. Sentiment Analysis
>   4. OCR
>   5. PII Redaction
{{% /notice %}}

### Architecture

![Amazon Bedrock (Sagemaker) LLMs with Amazon Opensearch Serverless](/images/arch-1.png)

### Architecture overview

{{%expand "Operational Excellence" %}}
The Serverless RAG demo pushes metrics to Amazon CloudWatch at various stages to provide observability into the infrastructure; Lambda functions, AI services, Amazon S3 buckets, and the rest of the solution components. Continuous integration and continuous delivery (CI/CD) and infrastructure deployment are managed in code through AWS App Runner.
{{% /expand%}}

{{%expand "Security" %}}
- Content designer UI app users are authenticated and authorized with Amazon Cognito.
- All inter-service communications use AWS Identity and Access Management (IAM) roles.
- All roles used by the solution follows least-privilege access. That is, it only contains minimum permissions required so the service can function properly.
- Communication end user using Amazon API Gateway and handed by Amazon Cognito.
- All data storage including Amazon S3 buckets have encryption at rest.
{{% /expand%}}

{{%expand "Reliability" %}}
- The solution uses AWS Serverless Services wherever possible (examples Lambda, API Gateway, Amazon S3, and Amazon OpenSearch Serverless) to ensure high availability and recovery from service failure.
- The solution protects against state machine definition errors by having automated tests performed on the solution.
{{% /expand%}}

{{%expand "Performance Efficiency" %}}
- The solution as mentioned earlier uses serverless architecture throughout this solution.
- The solution can be launched in any Region that supports AWS services in this solution such as: AWS Lambda, Amazon API Gateway, AWS S3, Amazon OpenSearch Services, Amazon Bedrock, and Amazon SageMaker.
{{% /expand%}}

{{%expand "Cost Optimization" %}}
- The solution uses serverless architecture therefore, customers only get charged for what they use.
- The compute layer defaults to AWS Lambda, so it provides pay per use. Amazon OpenSearch Serverless indexes are selected to reduce throughput cost for queries.
{{% /expand%}}

{{%expand "Sustainability" %}}
The solution utilizes managed and serverless services, to minimize the environmental impact of the backend services. A critical component for sustainability provided by the solution is maximizing the usage of the AWS AI services. The solution Serverless design (using Lambda and Amazon OpenSearch Serverless) and the use of managed services (such as AWS App Runner) are aimed at reducing carbon footprint compared to the footprint of continually operating on-premises servers.
{{% /expand%}}

### Content

1. [Prerequisites](1-prerequisites/)
2. [Deploying the Solution to your AWS account with AWS Cloudshell](2-deploy/)
3. [(Advanced) Using an existing Bedrock Knowledge base](3-advanced/)
