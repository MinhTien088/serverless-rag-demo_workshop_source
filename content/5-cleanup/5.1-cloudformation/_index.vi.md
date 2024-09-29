---
title: "CloudFormation"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

1. Truy cập [AWS Console](https://console.aws.amazon.com/console), tìm dịch vụ **CloudFormation**

![](/images/5.cleanup/0001-cloudformation.png)

2. Tại side bar, chọn **Stack**, chọn stack cần xoá, nhấn **Delete**

![](/images/5.cleanup/0002-cloudformation.png)

3. Tiếp tục nhấn **Delete** để xác nhận xoá stack

![](/images/5.cleanup/0003-cloudformation.png)

{{% notice info %}}
Dựa vào các bước hướng dẫn trên, xoá lần lượt theo thứ tự các stack sau:
{{% /notice %}}

> 1. AppRunnerHostingdevStack
> 2. ApiGwLlmsLambdadevStack
> 3. LlmsWithServerlessRagdevStack
> 4. CDKToolkit

{{% notice warning %}}
**Xoá lần lượt theo thứ tự nhé**, không cần quan tâm các stack Nested (vì các stack Nested sẽ tự động xoá theo stack chính)
{{% /notice %}}

Tiếp tục, chúng ta sẽ dọn dẹp tài nguyên cho dịch vụ [Amazon Cognito](5-cleanup/5.2-cognito/).
