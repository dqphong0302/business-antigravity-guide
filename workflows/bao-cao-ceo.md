---
description: "Vẽ tóm tắt Bức Tranh Lãi/Lỗ hằng ngày vào group Telegram của BOD"
---

# Lệnh: `/bao-cao-ceo`

**Phòng ban:** Ban Giám Đốc (BOD) & Khối Vận Hành (COO)

## Kịch Bản Luồng Chạy (Workflow Execution)

1. Hoạt động như 1 cronjob lúc 06:00 AM sáng.
// turbo
2. Đọc file `Doanh_So.xlsx` từ phòng Sales và check Cổng Thanh toán điện tử (API NH).
// turbo
3. Đọc dữ liệu biến động tồn kho ERP trong 24h.
// turbo
4. Chạy `bao_cao_ceo` để xuất ra 1 Thông điệp ngắn chứa Bullet Điểm tin Sáng, Cảnh báo Cháy kho/Mất doanh thu do Khách BOOM Hàng.
// turbo
5. Push Message qua Bot Telegram vào group "C-Level Hội Đồng Đáng Nhớ".
