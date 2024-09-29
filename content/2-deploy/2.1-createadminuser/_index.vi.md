---
title: "Tạo Người dùng Quản trị để triển khai stack"
date: "`r Sys.Date()`" 
weight: 1 
chapter: false
pre: " <b> 2.1. </b> "
---

#### Phần 1 - Tạo người dùng IAM với quyền Quản trị viên (TÙY CHỌN: Nếu bạn đã có vai trò Quản trị viên, bạn có thể bỏ qua bước này)

1. Tìm kiếm dịch vụ **IAM** trên [Bảng điều khiển AWS](https://console.aws.amazon.com/console) và truy cập vào **IAM Dashboard**

![IAM](/images/2.deploy/0001-createadminuser.png)

2. Nhấp vào tab **Roles** dưới mục **Access management** và nhấp vào **Create role**

![Create Role 1](/images/2.deploy/0002-createadminuser.png)

3. Chọn **AWS Account** và nhấp **Next**

![Create Role 2](/images/2.deploy/0003-createadminuser.png)

4. Trong phần permissions, chọn **AdministratorAccess**

![Create Role 3](/images/2.deploy/0004-createadminuser.png)

5. Đặt tên và mô tả cho role, ví dụ: `Deploy-Admin` và nhấp vào **Create role**

![Create Role 4](/images/2.deploy/0005-createadminuser.png)

6. Bây giờ bạn có thể đảm nhận role này và tiến hành triển khai stack. Nhấp vào **Switch role**

![Switch Role 1](/images/2.deploy/0006-createadminuser.png)

7. Cung cấp display name tuỳ ý và nhấp vào **Switch Role**

![Switch Role 2](/images/2.deploy/0007-createadminuser.png)

8. Tiếp tục đến bước CloudShell
