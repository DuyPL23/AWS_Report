---
title: "Bản đề xuất"
date: 2025-09-16
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# Studying English Website   

### 1. Tóm tắt điều hành  
Studying English Website được thiết kế dành cho các bạn học tiếng anh nhằm nâng cao khả năng học từ vựng, ngữ pháp và giao tiếp hằng ngày. Nền tảng tận dụng các dịch vụ AWS Serverless để cung cấp giám sát thời gian học tập, phân tích dự đoán khả năng học người học để đưa ra những chính sách học tập theo trình từ cơ bản đến nâng cao và tiết kiệm chi phí ở mức thấp nhất. 

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Tiếng anh là ngoại ngữ thiết yếu cho công việc và đời sống. Tuy nhiên, người học đang không có không gian và môi trường luyện tập, đặc biệt là trong việc giao tiếp. 

*Giải pháp*  

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Giải pháp tạo nền tảng cơ bản để các thành viên phòng lab phát triển một nền tảng IoT lớn hơn, đồng thời cung cấp nguồn dữ liệu cho những người nghiên cứu AI phục vụ huấn luyện mô hình hoặc phân tích. Nền tảng giảm bớt báo cáo thủ công cho từng trạm thông qua hệ thống tập trung, đơn giản hóa quản lý và bảo trì, đồng thời cải thiện độ tin cậy dữ liệu. Chi phí hàng tháng ước tính 0,66 USD (theo AWS Pricing Calculator), tổng cộng 7,92 USD cho 12 tháng. Tất cả thiết bị IoT đã được trang bị từ hệ thống trạm thời tiết hiện tại, không phát sinh chi phí phát triển thêm. Thời gian hoàn vốn 6–12 tháng nhờ tiết kiệm đáng kể thời gian thao tác thủ công.  

### 3. Kiến trúc giải pháp  
  

![Studying English Website Architecture]()

![Studying English Website Architecture]()

*Dịch vụ AWS sử dụng*  
- *AWS S3*: Lưu trữ dữ liệu thô (data lake) dữ liệu đã  xử lý (2 bucket)
- *AWS Amplify gen 2*: Lưu trữ giao diện web  
- *AWS MediaConvert*: Chuyển đổi video/audio.  
- *AWS Route53*: Quản lý DNS và định tuyến. 
- *AWS Cognitor*: Xác thực và quản lý người dùng.
- *AWS Secret manager*: Lưu trữ và bảo mật thông tin nhạy cảm.
- *AWS IAM*: Quản lý quyền truy cập AWS.
- *AWS Lambda*: Chạy code serverless theo sự kiện.
- *AWS WAF*: Bảo vệ ứng dụng web khỏi tấn công. 

*Thiết kế thành phần*  
- *Triển khai kỹ thuật*:  
- *Các giai đoạn triển khai*:     
- *Dự án gồm*:   
- *Xử lý dữ liệu*: AWS Glue Crawlers lập chỉ mục dữ liệu; ETL jobs chuyển đổi để phân tích.  
- *Giao diện web*: AWS Amplify lưu trữ ứng dụng Next.js cho bảng điều khiển và phân tích thời gian thực.  
- *Quản lý người dùng*: Amazon Cognito giới hạn 5 tài khoản hoạt động.  

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án gồm 2 phần — thiết lập trạm thời tiết biên và xây dựng nền tảng thời tiết — mỗi phần trải qua 4 giai đoạn:  
1. *Nghiên cứu và vẽ kiến trúc*: Nghiên cứu Raspberry Pi với cảm biến ESP32 và thiết kế kiến trúc AWS Serverless (1 tháng trước kỳ thực tập).  
2. *Tính toán chi phí và kiểm tra tính khả thi*: Sử dụng AWS Pricing Calculator để ước tính và điều chỉnh (Tháng 1).  
3. *Điều chỉnh kiến trúc để tối ưu chi phí/giải pháp*: Tinh chỉnh (ví dụ tối ưu Lambda với Next.js) để đảm bảo hiệu quả (Tháng 2).  
4. *Phát triển, kiểm thử, triển khai*: Lập trình Raspberry Pi, AWS services với CDK/SDK và ứng dụng Next.js, sau đó kiểm thử và đưa vào vận hành (Tháng 2–3).  

*Yêu cầu kỹ thuật*  
- *Trạm thời tiết biên*: Cảm biến (nhiệt độ, độ ẩm, lượng mưa, tốc độ gió), vi điều khiển ESP32, Raspberry Pi làm thiết bị biên. Raspberry Pi chạy Raspbian, sử dụng Docker để lọc dữ liệu và gửi 1 MB/ngày/trạm qua MQTT qua Wi-Fi.  
- *Nền tảng thời tiết*: Kiến thức thực tế về AWS Amplify (lưu trữ Next.js), Lambda (giảm thiểu do Next.js xử lý), AWS Glue (ETL), S3 (2 bucket), IoT Core (gateway và rules), và Cognito (5 người dùng). Sử dụng AWS CDK/SDK để lập trình (ví dụ IoT Core rules tới S3). Next.js giúp giảm tải Lambda cho ứng dụng web fullstack.  

### 5. Lộ trình & Mốc triển khai  
- *Trước thực tập (Tháng 0)*: lên kế hoạch học tập  
- *Thực tập (Tháng 1–3)*:  
    - Tháng 1: Học AWS và nâng cấp phần cứng.  
    - Tháng 2: Học cách triển khai, lên kế hoạch và vẽ kiến trúc  
    - Tháng 3: Triển khai, kiểm thử và đưa vào sử dụng   
- *Sau triển khai*: Nghiên cứu tiềm năng phát triển và chức năng mới cho chương trình 
Ước tính ngân sách  

### 6. Ước tính ngân sách  
Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Hoặc tải [tệp ước tính ngân sách](../attachments/budget_estimation.pdf).  

*Chi phí hạ tầng*  
- AWS S3: 0,15 USD/tháng (6 GB, 2 bucket, 2.100 request)
- AWS Amplify gen 2: 0,35 USD/tháng (256 MB, request 500 ms)  
- AWS MediaConvert: 0,05 USD/tháng (chuyển đổi video nhỏ)  
- AWS Route53: 0,50 USD/tháng (1 domain, 1 triệu query)  
- AWS Cognito: 0,00 USD/tháng (5 người dùng Free tier) 
- AWS Secrets Manager: 0,40 USD/tháng (10 secrets)
- AWS IAM: 0 USD/tháng
- AWS Lambda: 0,00 USD/tháng (1.000 request, 512 MB RAM)
- AWS WAF: 5,00 USD/tháng (1 Web ACL cơ bản)

*Tổng*: 6,45 USD/tháng, ~77,4 USD/12 tháng  
- *Phần cứng*: 265 USD một lần (Raspberry Pi  và cảm biến).  

### 7. Đánh giá rủi ro  
*Ma trận rủi ro*  
- Sập server: Ảnh hưởng cao, xác xuất trung bình  
- Vượt ngân sách: Ảnh hưởng trung bình, xác suất cao   

*Chiến lược giảm thiểu*  
- Chỉ phí: sử dụng AWS Budget để cảnh báo, tối ưu dịch vụ 

*Kế hoạch dự phòng*  
- Quay lại thu thập thủ công nếu AWS gặp sự cố.  
- Sử dụng CloudFormation để khôi phục cấu hình liên quan đến chi phí.  

### 8. Kết quả kỳ vọng  
*Cải tiến kỹ thuật*: Dữ liệu và phân tích thời gian thực thay thế quy trình thủ công. Có thể mở rộng tới 10–15 trạm.  
*Giá trị dài hạn*: Nền tảng dữ liệu 1 năm cho nghiên cứu AI, có thể tái sử dụng cho các dự án tương lai.
