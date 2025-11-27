---
title: "Blog 1"
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
<<<<<<< HEAD

=======
>>>>>>> b7de5673aac2db44e5dd308db089903344ed1d89
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

<<<<<<< HEAD
# Shorthills AI kết hợp với AWS và sử dụng DataStax để chuyển đổi cách tìm kiếm dữ liệu trong doanh nghiệp

Bởi Ganesh Sawhney | vào ngày 13 tháng 6 năm 2025

## Giới thiệu 

Khai thác giá trị từ data phi cấu trúc vẫn là một thách thức đối với các tổ chức. Họ gặp khó khăn trong việc trích xuất giá trị từ emails, báo cáo, tài liệu pháp lý và các tài sản số, dẫn đến việc ra quyết định bị chậm trễ. Theo nghiên cứu năm 2023 của IDC, 90% dữ liệu được tạo ra bởi doanh nghiệp là dữ liệu phi cấu trúc, chỉ có 10% là dữ liệu có cấu trúc. 

Các tổ chức cần những giải pháp tiên tiến như **vector search** và **graph indexing** để chuyển đổi dữ liệu petabyte phi cấu trúc thành thông tin có thể actionable. Khách hàng cũng cần các năng lực như tóm tắt tự động và phản hồi theo ngữ cảnh dựa trên dữ liệu của tổ chức.

Bài viết này giải thích cách mà sự hợp tác giữa Shorthills AI với AWS và Astra DB của DataStax đã ứng dụng các công nghệ tìm kiếm tiên tiến và xử lý ngôn ngữ tự nhiên (NLP) cho tìm kiếm doanh nghiệp. Giải pháp giúp khách hàng đưa ra quyết định kinh doanh dựa trên dữ liệu bằng cách tận dụng các tính năng bảo mật cấp doanh nghiệp của AWS kết hợp với khả năng **vector search** cùng hiệu năng cao của DataStax.

## Nhu cầu và cơ hội kinh doanh

Các ngành pháp lý, thương mại điện tử, y tế và dịch vụ tài chính phụ thuộc vào dữ liệu để đưa ra các quyết định chiến lược và tối ưu hóa mức độ gắn kết với khách hàng. Những dữ liệu này bao gồm bản án pháp lý, đánh giá, hóa đơn ở dạng PDF và tài liệu. Các kỹ thuật tiên tiến như vector search và graph indexing là cần thiết để xử lý khối dữ liệu này.

Shorthills AI đã phát triển một chatbot tối ưu hóa theo từng lĩnh vực dựa trên khung **RAG (Retrieval-Augmented Generation)** và **knowledge graph** để mang lại thông tin chuyên sâu được hỗ trợ bởi AI. Giải pháp giúp luật sư, chuyên gia tư vấn pháp lý, bác sĩ, chuyên gia y tế, quản lý sản phẩm thương mại điện tử giành lợi thế cạnh tranh nhờ các quyết định dựa trên dữ liệu.

Theo sự đẩy nhanh chuyển đổi số của các tổ chức, nhu cầu về giải pháp AI linh hoạt, an toàn và có khả năng mở rộng đã trở thành yếu tố thiết yếu. Thông qua việc hợp tác với AWS và DataStax, Shorthills AI mang đến cho khách hàng một giải pháp mạnh mẽ, giúp giảm 70% thời gian tìm kiếm so với các phương pháp truyền thống.

## Tổng quan giải pháp

Shorthills AI đã chuyển đổi từ các giải pháp open source sang **Astra DB trên AWS**. Sự chuyển đổi này cho phép triển khai khả năng tìm kiếm AI, mang đến cho khách hàng thông tin chuyên sâu theo thời gian thực. Giải pháp chuẩn hóa dữ liệu phi cấu trúc thông qua parsing và chunking, sau đó áp dụng NLP nâng cao, vector search và thuật toán đồ thị như **Degree Centrality** và **Article Rank**.  

Nhờ đó, giải pháp có thể trích xuất metadata, khám phá các relationships và cung cấp thông tin chuyên sâu từ dữ liệu trong datalake. Giải pháp này giúp doanh nghiệp thu được thông tin phù hợp về phán quyết pháp lý, cảm nhận khách hàng và xu hướng thị trường.

### Các tính năng nổi bật

- **Tùy chỉnh theo ngành**: Pháp lý, y tế, thương mại điện tử, v.v.  
- **Xử lý dữ liệu tối ưu**: Chunking tối ưu để xử lý hiệu quả dữ liệu lớn  
- **Khả năng hiểu nâng cao**: Graph-based indexing nắm bắt mối quan hệ phức tạp  
- **Thích ứng thời gian thực**: Incremental update trong OptimizeRAG cho dữ liệu mới

### So sánh hiệu năng

| Mô hình      | Comprehensiveness | Diversity | Empowerment | Overall |
| ------------ | ---------------- | --------- | ----------- | ------- |
| NaiveRAG     | 19.05%           | 10.98%    | 17.59%      | 17.46%  |
| OptimizeRAG  | 80.95%           | 89.02%    | 82.41%      | 82.54%  |

### Lợi ích cốt lõi

- **Nâng cao độ chính xác tìm kiếm**: Kết hợp nhiều mô hình, graph building, vector search  
- **Giảm chi phí quản lý**: Giảm 50% TCO nhờ Astra DB trên AWS  
- **Bảo mật dữ liệu**: AWS KMS, Amazon VPC endpoints, vector search production-ready

## Mô hình kiến trúc

- Dữ liệu vào **Amazon S3**  
- **Amazon Textract** trích xuất văn bản và dữ liệu  
- Lambda chia nhỏ (chunk) văn bản  
- LLMs (Amazon Bedrock) xử lý entity và relationships  
- Embeddings lưu trong **Astra DB**  
- **AWS Step Functions** điều phối workflow

### Các bước:

1. **Lưu trữ dữ liệu**: S3 bucket + EventBridge + CSV check  
2. **Chia khối dữ liệu và trích xuất entity-relationship**: Amazon Bedrock  
3. **Tạo và lưu trữ embedding**: Neptune cho entity-relationship, Astra DB cho vector

## Kết luận

Sử dụng vector search của **DataStax Astra DB** và tính năng bảo mật AWS, Shorthills AI mang đến giải pháp tìm kiếm dữ liệu có khả năng mở rộng, tuân thủ và hiệu năng vượt trội.

## Call to Action

Liên hệ đội ngũ Shorthills AI hoặc tham khảo AWS Startup Showcase và gian hàng DataStax trên AWS Marketplace.
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
