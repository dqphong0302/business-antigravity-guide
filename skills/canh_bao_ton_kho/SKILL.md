---
name: Cảnh Báo Tồn Kho Thấp (Inventory Alert System)
description: Quét file tồn kho định kỳ, phát hiện mặt hàng dưới ngưỡng an toàn, tự động gửi cảnh báo đặt hàng cho Bộ phận Mua hàng.
---

# Skill: Hệ Thống Cảnh Báo Tồn Kho Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Quản lý Kho hoặc Bộ phận Mua hàng cần giám sát mức tồn kho để tránh hết hàng hoặc tồn ứ đọng.

## Quy Trình Thực Hiện

1. Đọc file Tồn kho (`ton_kho.xlsx`): Mã SP, Tên, Số lượng hiện tại, Ngưỡng tối thiểu.
2. Lọc các mặt hàng có Số lượng <= Ngưỡng tối thiểu → Danh sách "Cần Đặt Hàng".
3. Lọc các mặt hàng không bán được >90 ngày → Danh sách "Hàng Ứ Đọng".
4. Vẽ biểu đồ thanh ngang: Top 10 mặt hàng sắp hết + Top 10 hàng ứ đọng.
5. Gửi cảnh báo qua Telegram/Email cho Trưởng nhóm Mua hàng.

## Lưu Ý

- Có thể cấu hình Cronjob để chạy tự động mỗi ngày lúc 7h sáng.
- Ngưỡng tối thiểu nên được cấu hình riêng cho từng loại mặt hàng.
