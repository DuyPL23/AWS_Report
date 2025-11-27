---
title: "Blog 3"
date: 2025-03-27
weight: 3
chapter: false
pre: " <b> 3.4. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Đơn giản hóa việc tích hợp private API với Amazon EventBridge và AWS Step Functions

Bởi Eric Johnson | ngày 27 tháng 3 năm 2025

Bài viết được viết bởi Pawan Puthran (Principal Specialist TAM – Serverless) và Vamsi Vikash Ankam (Senior Serverless Solutions Architect – Serverless).

## Giới thiệu

Vào tháng 12 năm 2024, AWS thông báo Amazon EventBridge và AWS Step Functions hỗ trợ tích hợp với các **private API** thông qua **AWS PrivateLink** và **Amazon VPC Lattice**. Tính năng này:

- Cho phép tích hợp liền mạch giữa mạng riêng, hạ tầng on-premises và cloud  
- Đơn giản hóa vận hành  
- Đảm bảo giao tiếp an toàn, kiểm soát giữa các dịch vụ bên trong VPC  

Bài viết này hướng dẫn cách tích hợp Step Functions với private API để các tương tác mạng riêng hiệu quả và an toàn hơn.

## Tổng quan

Trước đây, EventBridge và Step Functions cần proxy (AWS Lambda, SQS) để gửi sự kiện tới ứng dụng HTTPS trong VPC. Hiện nay, bạn có thể gọi trực tiếp **HTTPS endpoints riêng tư** chạy bên trong VPC.

### Lợi ích

1. **Bảo mật và tuân thủ**: Giữ API trong mạng riêng, giảm rủi ro Internet, đáp ứng các quy định ngành như tài chính và y tế.  
2. **Đơn giản hóa kiến trúc**: Loại bỏ proxy và thiết lập mạng phức tạp, giúp lập trình viên tập trung vào logic cốt lõi.  
3. **Hiệu suất và độ tin cậy**: Kết nối trực tiếp trong AWS backbone network, tăng tốc độ, giảm lỗi và phụ thuộc mạng ngoài.

## Thành phần kiến trúc

- **Resource Gateway**: Điểm vào an toàn cho dữ liệu tới tài nguyên trong VPC.  
- **Resource Configuration**: Xác định tài nguyên và quyền truy cập.  
- **EventBridge Connections**: Tạo kết nối tới HTTPS private endpoints thông qua resource configuration.  
- **AWS Resource Access Manager (RAM)**: Chia sẻ resource configuration an toàn giữa các tài khoản.

## Workload overview

Ví dụ workflow Step Functions phân loại đánh giá sản phẩm:

- Gọi **Amazon Nova Micro** qua Amazon Bedrock để phân loại review.  
- Nếu review giả → gửi sự kiện tới EventBridge bus  
- Nếu review thật → gọi **private HTTPS endpoint** trong VPC (host trên AWS Fargate, sau ALB nội bộ).

### Hình 1: Workflow của Step Functions gọi private endpoint HTTPS

Workflow phân tích văn bản, hành vi người dùng và tín hiệu ngôn ngữ để xác định độ xác thực. Các review đáng ngờ tự động đánh dấu thông qua workflow tùy chỉnh.

## Triển khai ví dụ

1. Tạo **Route 53 public hosted zone** (ví dụ: api.com) và chứng chỉ ACM.  
2. Sử dụng ứng dụng mẫu kèm hướng dẫn triển khai.  

### Tình huống 1: Một tài khoản

- Step Functions, EventBridge Connections, private resources nằm cùng tài khoản.  
- **Resource Gateway**: Điểm vào cho private resources, phủ nhiều subnet để HA.  
- **Resource Configurations**: Thiết lập kết nối private endpoint → Gateway.  
- **EventBridge Connection**: Cho Step Functions kết nối private API.  

Ví dụ payload kiểm thử Step Functions:

```json
{
  "items": [
    {
      "asin": "B000FA64PA",
      "helpful": [0, 0],
      "overall": 5,
      "reviewText": "Darth Maul working under cloak of darkness...",
      "reviewTime": "10 11, 2013",
      "unixReviewTime": 1381449600
    },
    {
      "asin": "B000F83SZQ",
      "helpful": [1, 1],
      "overall": 4,
      "reviewText": "Never heard of Amy Brewster...",
      "reviewTime": "03 22, 2014",
      "unixReviewTime": 1395446400
    }
  ]
}
