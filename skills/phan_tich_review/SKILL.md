---
name: Phân Tích Đánh Giá Khách Hàng (Customer Review Analysis)
description: Thu thập và phân tích đánh giá/review từ khách hàng (từ file hoặc web), phân loại Tích cực/Tiêu cực, tìm ra vấn đề phổ biến nhất.
---

# Skill: Phân Tích Đánh Giá Khách Hàng (Sentiment Analysis)

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Marketing/CSKH cần hiểu khách hàng đang nói gì về sản phẩm: Khen gì, Chê gì, Muốn gì.

## Quy Trình Thực Hiện

1. Đọc nguồn dữ liệu review (file CSV export từ Shopee/Google Reviews, hoặc cào từ web).
2. Phân loại mỗi review thành: Tích cực (Positive), Tiêu cực (Negative), Trung tính (Neutral).
3. Trích xuất Keywords phổ biến nhất trong nhóm Tiêu cực (ví dụ: "giao chậm", "đóng gói kém").
4. Vẽ biểu đồ tròn (Pie Chart): Tỷ lệ Tích cực vs Tiêu cực.
5. Vẽ Word Cloud (Đám mây từ khóa) cho nhóm Tiêu cực để nhìn nhanh vấn đề.
6. Xuất báo cáo `PhanTich_Review.xlsx` + ảnh biểu đồ.

## Lưu Ý

- Không công khai tên/thông tin cá nhân của người đánh giá.
- Với review tiếng Việt có viết tắt/teencode, cần xử lý chuẩn hóa trước khi phân tích.
