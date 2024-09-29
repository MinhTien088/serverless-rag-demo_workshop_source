---
title: "Áp dụng cơ sở kiến thức vào Serverless RAG demo"
date: "`r Sys.Date()`" 
weight: 2 
chapter: false
pre: " <b> 4.2. </b> "
---

1. Lấy các thông tin về **Embeddings model**, **Collection ARN** và **Vector index name** được sử dụng bởi cơ sở kiến thức hiện có trên Bedrock

![Collection-ARN](/images/4.advanced/0012-createknowledgebase.png)

2. Truy cập [AWS Console](https://console.aws.amazon.com/console), tìm dịch vụ **Amazon OpenSearch**

![](/images/4.advanced/0001-applyknowledgebase.png)

3. Truy cập Amazon OpenSearch Serverless và tìm kiếm bằng ARN để lấy Endpoint OpenSearch

![](/images/4.advanced/0002-applyknowledgebase.png)

![OSS-Endpoint](/images/4.advanced/0003-applyknowledgebase.png)

4. Tìm ID của model Embedding được sử dụng bởi Bedrock KB từ [đây](https://docs.aws.amazon.com/bedrock/latest/userguide/model-ids.html)

![](/images/4.advanced/0013-applyknowledgebase.png)

5. Truy cập [AWS Console](https://console.aws.amazon.com/console), tìm dịch vụ **Lambda**

![](/images/4.advanced/0014-applyknowledgebase.png)

6. Tìm hàm lambda `bedrock_rag_query_`, sau đó tiến thành các bước thiết lập sau

![](/images/4.advanced/0015-applyknowledgebase.png)

- Chọn tab **Configuration**
- Chọn **Environment variables**
- Nhấn **Edit**

![](/images/4.advanced/0011-applyknowledgebase.png)

Thiết lập như sau:
   
   a. **IS_BEDROCK_KB** = `yes`  

   b. **OPENSEARCH_VECTOR_ENDPOINT** = <<Endpoint Amazon OpenSearch Serverless của Bedrock KB hiện có>> (không bao gồm **https://**)

   c. **EMBED_MODEL_ID** = <<ID Mô hình Embedding được sử dụng bởi Bedrock KB hiện có>>

   d. **VECTOR_INDEX_NAME** = <<VECTOR_INDEX được sử dụng bởi Bedrock KB hiện có>>

   ![Lambda-Config](/images/4.advanced/0012-applyknowledgebase.png)

- Sau đó nhấn **Save**

7. Lấy ARN của Lambda role

- Chọn tab **Configuration**
- Chọn **Permissions**
- Nhấn vào đường dẫn tại Role name

![Lambda-Config](/images/4.advanced/0006-applyknowledgebase.png)

- Tại giao diện role, note lại ARN của role đó

![Lambda-Config](/images/4.advanced/0007-applyknowledgebase.png)

8. Quay lại tab Amazon OpenSearch tại bước 3. Tại phần **Data access**, truy cập vào đường dẫn **Associated policy**, sau đó nhấn **Edit**

![Lambda-Config](/images/4.advanced/0004-applyknowledgebase.png)

![Lambda-Config](/images/4.advanced/0005-applyknowledgebase.png)

9. Chọn **Add principals**, nhấn **IAM users and roles**

![Lambda-Config](/images/4.advanced/0008-applyknowledgebase.png)

- Cung cấp ARN của role đã note ở bước 7, sau đó nhấn **Save**

![Lambda-Config](/images/4.advanced/0009-applyknowledgebase.png)

- Hoàn tất

![Lambda-Config](/images/4.advanced/0010-applyknowledgebase.png)

10. Bây giờ hãy thử Document Chat trên giao diện người dùng, nó sẽ truy vấn từ cơ sở kiến thức Amazon Bedrock.

![Lambda-Config](/images/4.advanced/0016-applyknowledgebase.jpg)
