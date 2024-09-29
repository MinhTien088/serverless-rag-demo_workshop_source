---
title: "Tạo cơ sở kiến thức Amazon Bedrock"
date: "`r Sys.Date()`" 
weight: 1 
chapter: false
pre: " <b> 4.1. </b> "
---

1. Truy cập [AWS Console](https://console.aws.amazon.com/console), tìm dịch vụ **Amazon Bedrock**

![](/images/4.advanced/0014-createknowledgebase.png)

2. Tại side bar, chọn **Knowledge bases**, sau đó nhấn chọn **Create knowledge base**

![](/images/4.advanced/0001-createknowledgebase.png)

3. Đặt tên cho cơ sở kiến thức (tuỳ chọn)

![](/images/4.advanced/0002-createknowledgebase.png)

4. Tại phần **Choose data source**, chọn **Web Crawler**, nhấn **Next**

![](/images/4.advanced/0003-createknowledgebase.png)

5. Đặt tên cho data source (tuỳ chọn). Tại phần **Source URLs**, nhập vào `https://gohugo.io/documentation/`, nhấn **Next**

![](/images/4.advanced/0004-createknowledgebase.png)

6. Tại phần **Embeddings model**, chọn **Embed Multilingual v3 - By Cohere**, nhấn **Next**

![](/images/4.advanced/0005-createknowledgebase.png)

7. Xem lại các thông tin đã thiết lập, nhấn **Create knowledge base**

![](/images/4.advanced/0006-createknowledgebase.png)

8. Sau khi cơ sở kiến thức được tạo xong, nhấn **Go to data sources**

![](/images/4.advanced/0007-createknowledgebase.png)

9. Chọn Data source hiện có, sau đó nhấn **Sync**

![](/images/4.advanced/0008-createknowledgebase.png)

Quá trình đồng bộ hoá dữ liệu sẽ diễn ra một lúc, nhanh chậm tuỳ vào nguồn dữ liệu đã cung cấp.

10. Sau khi hoàn tất quá trình đồng bộ dữ liệu, chúng ta sẽ tiến hành test thử cơ sở kiến thức.

- Nhấn **Select model**

![](/images/4.advanced/0009-createknowledgebase.png)

- Chọn **Model providers** là **Anthropic**
- Chọn model **Claude 3.5 Sonnet**
- Nhấn **Apply**

![](/images/4.advanced/0010-createknowledgebase.png)

- Nhập câu hỏi và kiểm tra câu trả lời

![](/images/4.advanced/0011-createknowledgebase.png)

11. Quá trình tạo cơ sở kiến thức đã hoàn tất. Chúng ta sẽ note lại các thông tin về **Embeddings model**, **Collection ARN** và **Vector index name**

![](/images/4.advanced/0012-createknowledgebase.png)
