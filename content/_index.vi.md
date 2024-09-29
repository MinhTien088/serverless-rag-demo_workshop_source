---
title: "Serverless RAG demo"
date: "`r Sys.Date()`" 
weight: 1 
chapter: false
---

# Giải pháp RAG và quy trình xây dựng agent có khả năng mở rộng với Amazon Bedrock và dịch vụ serverless Amazon Opensearch

### Tổng quan

Sự phổ biến của AI đang được thúc đẩy bởi các mô hình AI tạo sinh có khả năng tạo ra nội dung giống con người. Tuy nhiên, các mô hình nền tảng này được đào tạo trên dữ liệu chung nên kém hiệu quả cho các tác vụ chuyên biệt. Đó là lý do tầm quan trọng của Tạo sinh Tăng cường Truy vấn (RAG). RAG cho phép bổ sung prompt bằng dữ liệu bên ngoài liên quan để có kết quả chuyên biệt hơn. Với RAG, tài liệu và truy vấn được chuyển đổi thành embedding, so sánh để tìm ngữ cảnh liên quan, và ngữ cảnh đó được thêm vào prompt gốc trước khi đưa vào mô hình ngôn ngữ lớn. Thư viện kiến thức có thể được cập nhật bất đồng bộ để cung cấp dữ liệu bên ngoài phù hợp nhất cho việc tăng cường prompt.

[Amazon OpenSearch Serverless (AOSS) cung cấp công cụ vector để lưu trữ embedding cho tìm kiếm tương đồng nhanh hơn](https://aws.amazon.com/blogs/big-data/introducing-the-vector-engine-for-amazon-opensearch-serverless-now-in-preview/). Công cụ vector này cung cấp khả năng tìm kiếm tương đồng đơn giản, có khả năng mở rộng và hiệu suất cao trong Amazon OpenSearch Serverless, giúp dễ dàng xây dựng ứng dụng AI tạo sinh mà không cần quản lý cơ sở hạ tầng cơ sở dữ liệu vector bên dưới.

{{% notice note %}}
Workshop này cung cấp giải pháp AI tạo sinh sẵn sàng cho môi trường sản xuất, dễ dàng triển khai với các tính năng sau:
>   1. Trò chuyện với tài liệu
>   2. Hợp tác multi-agent
>   3. Phân tích cảm xúc
>   4. Nhận dạng ký tự quang học (OCR)
>   5. Ẩn thông tin cá nhân
{{% /notice %}}

<!-- {{% notice info %}}
Giao diện người dùng cũ được duy trì trong nhánh v0.0.1(Old-UI).
{{% /notice %}} -->

<!-- #### Các demo

{{%expand "Trò chuyện với tài liệu/Quản lý tài liệu (Đa ngôn ngữ)" %}}
![Doc Chat/Doc Management (Multi-lingual) gif demo](/images/demo_doc-chat-management.gif)
{{% /expand%}}

{{%expand "Demo multi-agent" %}}
![Multi-Agent gif demo](/images/demo_multi-agent.gif)
{{% /expand%}}

{{%expand "Ẩn thông tin cá nhân" %}}
![]()
{{% /expand%}}

{{%expand "OCR" %}}
![Multi-Agent gif demo](/images/demo_multi-agent.gif)
{{% /expand%}}

{{%expand "Phân tích cảm xúc" %}}
![]()
{{% /expand%}} -->

### Kiến trúc

![Amazon Bedrock (Sagemaker) LLMs with Amazon Opensearch Serverless](/images/arch-1.png)

### Tổng quan kiến trúc

{{%expand "Vận hành xuất sắc" %}} Demo Serverless RAG đẩy các chỉ số đo lường đến Amazon CloudWatch ở nhiều giai đoạn khác nhau để cung cấp khả năng quan sát vào cơ sở hạ tầng; các hàm Lambda, dịch vụ AI, bucket Amazon S3 và các thành phần còn lại của giải pháp. Tích hợp liên tục và phân phối liên tục (CI/CD) và triển khai cơ sở hạ tầng được quản lý trong mã thông qua AWS App Runner. {{% /expand%}}

{{%expand "Bảo mật" %}}
- Người dùng ứng dụng giao diện thiết kế nội dung được xác thực và ủy quyền với Amazon Cognito.
- Tất cả các giao tiếp giữa các dịch vụ sử dụng vai trò AWS Identity and Access Management (IAM).
- Tất cả các vai trò được sử dụng bởi giải pháp đều tuân theo quyền truy cập tối thiểu. Nghĩa là, nó chỉ chứa các quyền tối thiểu cần thiết để dịch vụ có thể hoạt động đúng.
- Giao tiếp với người dùng cuối sử dụng Amazon API Gateway và được xử lý bởi Amazon Cognito.
- Tất cả các lưu trữ dữ liệu bao gồm các bucket Amazon S3 đều có mã hóa khi được lưu trữ.
{{% /expand%}}

{{%expand "Độ tin cậy" %}}
- Giải pháp sử dụng các dịch vụ Serverless của AWS sẵn sàng bất cứ khi nào có thể (ví dụ như Lambda, API Gateway, Amazon S3 và Amazon OpenSearch Serverless) để đảm bảo khả năng sẵn sàng cao và khôi phục từ lỗi dịch vụ.
- Giải pháp bảo vệ chống lại các lỗi định nghĩa máy trạng thái bằng cách thực hiện các bài kiểm tra tự động trên giải pháp.
{{% /expand%}}

{{%expand "Hiệu quả về hiệu suất" %}}
- Như đã đề cập trước đó, giải pháp sử dụng kiến trúc serverless xuyên suốt giải pháp này.
- Giải pháp có thể được triển khai ở bất kỳ khu vực nào hỗ trợ các dịch vụ AWS trong giải pháp này như: AWS Lambda, Amazon API Gateway, AWS S3, Amazon OpenSearch Services, Amazon Bedrock và Amazon SageMaker.
{{% /expand%}}

{{%expand "Tối ưu hóa chi phí" %}}
- Giải pháp sử dụng kiến trúc serverless, do đó, khách hàng chỉ phải trả tiền cho những gì họ sử dụng.
- Lớp tính toán mặc định là AWS Lambda, vì vậy nó cung cấp khả năng thanh toán theo mức sử dụng. Các chỉ mục Amazon OpenSearch Serverless được chọn để giảm chi phí thông lượng cho các truy vấn.
{{% /expand%}}

{{%expand "Tính bền vững" %}}
Giải pháp sử dụng các dịch vụ được quản lý và serverless để giảm thiểu tác động môi trường của các dịch vụ backend. Một thành phần quan trọng cho tính bền vững được cung cấp bởi giải pháp là tối đa hóa việc sử dụng các dịch vụ AI của AWS. Thiết kế Serverless của giải pháp (sử dụng Lambda và Amazon OpenSearch Serverless) và việc sử dụng các dịch vụ được quản lý (chẳng hạn như AWS App Runner) nhằm mục đích giảm dấu chân carbon so với dấu chân carbon của các máy chủ on-premises hoạt động liên tục.
{{% /expand%}}

### Nội dung

1. [Chuẩn bị](1-prerequisites/)
2. [Triển khai giải pháp vào tài khoản AWS bằng AWS Cloudshell](2-deploy/)
3. [(Nâng cao) Sử dụng cơ sở kiến thức Amazon Bedrock có sẵn](3-advanced/)
