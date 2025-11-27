---
title: "Blog 2"
date: 2025-09-18
weight: 2
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

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
