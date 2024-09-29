---
title: "Triển khai Giải pháp dựa trên RAG"
date: "`r Sys.Date()`" 
weight: 2 
chapter: false
pre: " <b> 2.2. </b> "
---

#### Phần 2 - Triển khai Giải pháp dựa trên RAG này (Các lệnh dưới đây nên được thực hiện trong khu vực triển khai)

1. Chuyển sang vai trò Admin. Tìm kiếm dịch vụ CloudShell trên AWS Console và làm theo các bước dưới đây để sao chép kho lưu trữ github

![CloudShell](/images/2.deploy/0001-deployragbasedsolution.png)

2. Sao chép kho lưu trữ serverless-rag-demo từ aws-samples bằng Git

```bash
git clone https://github.com/aws-samples/serverless-rag-demo.git
```

![git clone https://github.com/aws-samples/serverless-rag-demo.git](/images/2.deploy/0002-deployragbasedsolution.png)

3. Di chuyển đến thư mục chứa các tệp đã tải xuống.

```bash
cd serverless-rag-demo
```

![cd serverless-rag-demo](/images/2.deploy/0003-deployragbasedsolution.png)

4. Chạy tập lệnh bash để tạo giải pháp dựa trên RAG. Truyền môi trường và khu vực để triển khai. Môi trường có thể là `dev`, `qa`, `sandbox` bằng cách chạy các lệnh khác nhau như `sh creator.sh dev`, `sh creator.sh qa` hoặc `sh creator.sh sandbox` (mặc định là *dev*). (Xem [Điều kiện tiên quyết](1-prerequisites/) để triển khai đến khu vực chính xác.)

```bash
sh creator.sh
```

![sh creator.sh](/images/2.deploy/0004-deployragbasedsolution.png)

5. Nhập `1` để chọn khu vực **N.Virginia**

![Chọn Khu vực](/images/2.deploy/0005-deployragbasedsolution.png)

6. Nhập `1` để chọn tùy chọn **Triển khai động cơ vector Amazon OpenSearch Serverless cho RAG**. Nhấn **Enter** để tiếp tục triển khai ngăn xếp hoặc **Ctrl + C** để thoát

![Chọn Tùy chọn](/images/2.deploy/0006-deployragbasedsolution.png)

7. Giao diện người dùng được lưu trữ trên AppRunner. Liên kết đến AppRunner có thể được tìm thấy trong CloudShell sau khi quá trình thực thi tập lệnh hoàn tất, hoặc bạn cũng có thể truy cập [dịch vụ AppRunner](https://console.aws.amazon.com/apprunner) trên AWS Console và lấy URL https. Giao diện người dùng được xác thực thông qua Amazon Cognito, do đó lần đầu tiên bạn sẽ phải đăng ký và sau đó đăng nhập vào ứng dụng

![trong CloudShell](/images/2.deploy/0007-deployragbasedsolution-2.png)

![trong Giao diện App Runner](/images/2.deploy/0007-deployragbasedsolution-1.png)

8. Trên trang Amazon Bedrock, kích hoạt quyền truy cập vào các mô hình dưới đây

![Truy cập mô hình Amazon Bedrock](/images/2.deploy/0008-deployragbasedsolution.png)
