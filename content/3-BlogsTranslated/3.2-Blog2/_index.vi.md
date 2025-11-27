---
title: "Blog 2"
<<<<<<< HEAD
date: 2025-09-18
weight: 2
chapter: false
pre: " <b> 3.3. </b> "
=======
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
>>>>>>> b7de5673aac2db44e5dd308db089903344ed1d89
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

<<<<<<< HEAD
# Đơn giản hóa việc tạo tài liệu mã nguồn với Amazon Q Developer

Bởi Jehu Gray, Joyce Muya, Adeogo Olajide, Abiola Olanrewaju, và Damola Oluyemo | vào ngày 11 tháng 4 năm 2005

## Giới thiệu

Trong thời gian phát triển phần mềm nhanh chóng, việc duy trì tài liệu chi tiết thường bị xếp sau so với ưu tiên phát triển tính năng. Agent `/doc` của Amazon Q Developer đã thay đổi điều đó bằng cách tự động hóa việc tạo và cập nhật tệp README. Công cụ này rút ngắn đáng kể thời gian viết tài liệu, giúp quá trình phát triển tính năng không bị gián đoạn.

## Cách Amazon Q Developer tạo tài liệu tự động

Agent `/doc` sử dụng **Generative AI** để phân tích toàn bộ mã nguồn và tự động tạo tài liệu chi tiết. Nó tuân thủ `.gitignore`, loại bỏ các tệp không cần tạo tài liệu.

## Tổng quan giải pháp

Ví dụ: Một nhóm hạ tầng đám mây làm việc trên dự án **AWS DataSync**. Khi quản lý sản phẩm yêu cầu tài liệu hướng dẫn chi tiết, nhóm sử dụng `/doc` để tự động tạo README, thay vì viết thủ công.

## Bắt đầu với `/doc`

Các bước cơ bản:  

1. **Cài đặt Amazon Q** theo hướng dẫn  
2. Mở IDE với phần mở rộng Amazon Q  
3. Nhấp vào biểu tượng Amazon Q để mở bảng trò chuyện  
4. Nhập lệnh `/doc` để bắt đầu quy trình tạo tài liệu  
5. Chọn tác vụ tài liệu:
   - Tạo README mới  
   - Cập nhật README hiện có

### Ví dụ: Tạo README mới

- Chọn “Create a README”  
- Xác nhận thư mục, chọn “Yes”  
- Agent sẽ quét mã nguồn, tóm tắt nội dung và tạo README  
- Xem trước tệp và chọn chấp nhận hoặc chỉnh sửa trước khi áp dụng

### Ví dụ: Cập nhật README hiện có

- Chọn “Update an existing README”  
- Mô tả các thay đổi cần thực hiện  
- Agent sẽ đề xuất cập nhật tài liệu dựa trên thay đổi gần nhất trong mã nguồn  
- Xác nhận các thay đổi bằng cách chọn “Yes”

## Quản lý tài liệu nâng cao

Agent `/doc` hỗ trợ lặp lại (iterative feedback loop):

- Xem xét nội dung để phát hiện thiếu sót  
- Cung cấp phản hồi cụ thể để tinh chỉnh  
- Yêu cầu bổ sung giải thích chi tiết  
- Xây dựng tài liệu hoàn chỉnh qua nhiều vòng cập nhật

### Tài liệu cho các thành phần cụ thể

- **README root-level**: Tổng quan dự án  
- **README component-level**: Chi tiết từng module  
- **Service-level**: Microservices  
- **API docs**: Giải thích giao diện và endpoints  

### Xử lý việc kế thừa tài liệu

- Tạo tài liệu cho dự án gốc (parent project)  
- Tạo tài liệu cho các phần mở rộng (extensions)  
- Cross-reference giữa các tài liệu  
- Cập nhật các phần cụ thể khi mẫu kế thừa thay đổi

### Chiến lược đồng bộ tài liệu

- Thiết lập lịch cập nhật tài liệu theo sprint  
- Gắn rà soát tài liệu vào quy trình **code review**  
- Sử dụng `/doc` để tạo bản tóm tắt thay đổi  
- Xác minh rằng tài liệu phản ánh đúng thay đổi mã nguồn

## Thực tiễn tốt nhất khi sử dụng `/doc`

1. **Tối ưu hóa repository**: Chọn tạo tài liệu cho toàn bộ hoặc từng phần của mã nguồn  
2. **Duy trì chất lượng mã**: Chú thích rõ ràng, tên biến/hàm có ý nghĩa, tuân thủ coding conventions  
3. **Mô tả rõ ràng khi yêu cầu thay đổi**: Sử dụng Update an existing README và Make a specific change  
4. **Soạn mô tả thay đổi hiệu quả**: Bao gồm phần cần chỉnh sửa, nội dung cần thêm/xóa, các vấn đề cần khắc phục  
5. **Hiểu giới hạn của hệ thống**: `/doc` không truy cập nền tảng nội bộ, phần mềm chuyên dụng, cần chỉnh sửa thủ công khi cần

### Quotas và giới hạn

- Giới hạn số lần phản hồi (feedback iterations) trong mỗi phiên  
- Bỏ qua các tệp/thư mục trong `.gitignore`

## Tổng kết

Amazon Q Developer `/doc` biến việc tạo tài liệu từ công việc tẻ nhạt thành tự động và hiệu quả. README luôn chính xác, cập nhật mà không tốn thời gian phát triển. `/doc` có thể tích hợp dễ dàng vào quy trình phát triển.

## Giới thiệu tác giả

### Jehu Gray
Prototyping Architect tại AWS, khám phá khả năng IaC.

### Abiola Olanrewaju
Solutions Architect tại AWS, chuyên hỗ trợ GovTech, Data Analytics, Security, Generative AI.

### Adeogo Olajide
Solutions Architect tại AWS, hỗ trợ GovTech và tổ chức công, chuyên thiết kế kiến trúc bảo mật, mở rộng, tuân thủ.

### Joyce Muya
Solutions Architect tại AWS, hỗ trợ doanh nghiệp truyền thông & giải trí, chuyên về Analytics và AI/ML workloads.

### Damola Oluyemo
Solutions Architect tại AWS, hỗ trợ doanh nghiệp, thiết kế giải pháp điện toán đám mây, khám phá IaC & Generative AI.
=======
# Bắt đầu với healthcare data lakes: Sử dụng microservices

Các data lake có thể giúp các bệnh viện và cơ sở y tế chuyển dữ liệu thành những thông tin chi tiết về doanh nghiệp và duy trì hoạt động kinh doanh liên tục, đồng thời bảo vệ quyền riêng tư của bệnh nhân. **Data lake** là một kho lưu trữ tập trung, được quản lý và bảo mật để lưu trữ tất cả dữ liệu của bạn, cả ở dạng ban đầu và đã xử lý để phân tích. data lake cho phép bạn chia nhỏ các kho chứa dữ liệu và kết hợp các loại phân tích khác nhau để có được thông tin chi tiết và đưa ra các quyết định kinh doanh tốt hơn.

Bài đăng trên blog này là một phần của loạt bài lớn hơn về việc bắt đầu cài đặt data lake dành cho lĩnh vực y tế. Trong bài đăng blog cuối cùng của tôi trong loạt bài, *“Bắt đầu với data lake dành cho lĩnh vực y tế: Đào sâu vào Amazon Cognito”*, tôi tập trung vào các chi tiết cụ thể của việc sử dụng Amazon Cognito và Attribute Based Access Control (ABAC) để xác thực và ủy quyền người dùng trong giải pháp data lake y tế. Trong blog này, tôi trình bày chi tiết cách giải pháp đã phát triển ở cấp độ cơ bản, bao gồm các quyết định thiết kế mà tôi đã đưa ra và các tính năng bổ sung được sử dụng. Bạn có thể truy cập các code samples cho giải pháp tại Git repo này để tham khảo.

---

## Hướng dẫn kiến trúc

Thay đổi chính kể từ lần trình bày cuối cùng của kiến trúc tổng thể là việc tách dịch vụ đơn lẻ thành một tập hợp các dịch vụ nhỏ để cải thiện khả năng bảo trì và tính linh hoạt. Việc tích hợp một lượng lớn dữ liệu y tế khác nhau thường yêu cầu các trình kết nối chuyên biệt cho từng định dạng; bằng cách giữ chúng được đóng gói riêng biệt với microservices, chúng ta có thể thêm, xóa và sửa đổi từng trình kết nối mà không ảnh hưởng đến những kết nối khác. Các microservices được kết nối rời thông qua tin nhắn publish/subscribe tập trung trong cái mà tôi gọi là “pub/sub hub”.

Giải pháp này đại diện cho những gì tôi sẽ coi là một lần lặp nước rút hợp lý khác từ last post của tôi. Phạm vi vẫn được giới hạn trong việc nhập và phân tích cú pháp đơn giản của các **HL7v2 messages** được định dạng theo **Quy tắc mã hóa 7 (ER7)** thông qua giao diện REST.

**Kiến trúc giải pháp bây giờ như sau:**

> *Hình 1. Kiến trúc tổng thể; những ô màu thể hiện những dịch vụ riêng biệt.*

---

Mặc dù thuật ngữ *microservices* có một số sự mơ hồ cố hữu, một số đặc điểm là chung:  
- Chúng nhỏ, tự chủ, kết hợp rời rạc  
- Có thể tái sử dụng, giao tiếp thông qua giao diện được xác định rõ  
- Chuyên biệt để giải quyết một việc  
- Thường được triển khai trong **event-driven architecture**

Khi xác định vị trí tạo ranh giới giữa các microservices, cần cân nhắc:  
- **Nội tại**: công nghệ được sử dụng, hiệu suất, độ tin cậy, khả năng mở rộng  
- **Bên ngoài**: chức năng phụ thuộc, tần suất thay đổi, khả năng tái sử dụng  
- **Con người**: quyền sở hữu nhóm, quản lý *cognitive load*

---

## Lựa chọn công nghệ và phạm vi giao tiếp

| Phạm vi giao tiếp                        | Các công nghệ / mô hình cần xem xét                                                        |
| ---------------------------------------- | ------------------------------------------------------------------------------------------ |
| Trong một microservice                   | Amazon Simple Queue Service (Amazon SQS), AWS Step Functions                               |
| Giữa các microservices trong một dịch vụ | AWS CloudFormation cross-stack references, Amazon Simple Notification Service (Amazon SNS) |
| Giữa các dịch vụ                         | Amazon EventBridge, AWS Cloud Map, Amazon API Gateway                                      |

---

## The pub/sub hub

Việc sử dụng kiến trúc **hub-and-spoke** (hay message broker) hoạt động tốt với một số lượng nhỏ các microservices liên quan chặt chẽ.  
- Mỗi microservice chỉ phụ thuộc vào *hub*  
- Kết nối giữa các microservice chỉ giới hạn ở nội dung của message được xuất  
- Giảm số lượng synchronous calls vì pub/sub là *push* không đồng bộ một chiều

Nhược điểm: cần **phối hợp và giám sát** để tránh microservice xử lý nhầm message.

---

## Core microservice

Cung cấp dữ liệu nền tảng và lớp truyền thông, gồm:  
- **Amazon S3** bucket cho dữ liệu  
- **Amazon DynamoDB** cho danh mục dữ liệu  
- **AWS Lambda** để ghi message vào data lake và danh mục  
- **Amazon SNS** topic làm *hub*  
- **Amazon S3** bucket cho artifacts như mã Lambda

> Chỉ cho phép truy cập ghi gián tiếp vào data lake qua hàm Lambda → đảm bảo nhất quán.

---

## Front door microservice

- Cung cấp API Gateway để tương tác REST bên ngoài  
- Xác thực & ủy quyền dựa trên **OIDC** thông qua **Amazon Cognito**  
- Cơ chế *deduplication* tự quản lý bằng DynamoDB thay vì SNS FIFO vì:
  1. SNS deduplication TTL chỉ 5 phút
  2. SNS FIFO yêu cầu SQS FIFO
  3. Chủ động báo cho sender biết message là bản sao

---

## Staging ER7 microservice

- Lambda “trigger” đăng ký với pub/sub hub, lọc message theo attribute  
- Step Functions Express Workflow để chuyển ER7 → JSON  
- Hai Lambda:
  1. Sửa format ER7 (newline, carriage return)
  2. Parsing logic  
- Kết quả hoặc lỗi được đẩy lại vào pub/sub hub

---

## Tính năng mới trong giải pháp

### 1. AWS CloudFormation cross-stack references
Ví dụ *outputs* trong core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
>>>>>>> b7de5673aac2db44e5dd308db089903344ed1d89
