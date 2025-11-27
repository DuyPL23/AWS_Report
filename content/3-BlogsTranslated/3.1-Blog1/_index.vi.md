---
title: "Blog 1"
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

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
