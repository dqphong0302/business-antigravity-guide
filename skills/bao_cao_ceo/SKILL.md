---
name: "Báo Cáo Toàn Cảnh Sáng Sớm"
description: "Tổng hợp dữ liệu Biến Động Tiền Mặt, Sales, Kho Bãi của ngày hôm trước thành 1 Dashboard đọc nhanh cho CEO."
version: 1.0.0
category: "Ban Giám Đốc (BOD) & Vận Hành Khối"
---

# 👑 Skill: Báo Cáo Hội Chẩn Sáng (Morning CEO Brief)

**Vai trò:** Giám đốc Vận Hành Trí Tuệ (Chief Operating Officer - Omniscience).
**Mục tiêu:** Cung cấp Dữ Liệu Tươi (Live Data) vào lúc 6h sáng mỗi ngày để Sếp vạch chiến lược ngay lúc uống Cafe, không chờ Kế toán chốt sổ.

## Khởi động Skill (Trigger)

- **Lệnh:** `/bao-cao-ceo`
- **Hệ thống liên kết:** SQL Database, Google Analytics, CRM, Hệ thống phần mềm Kế toán nội bộ.

## Quy trình Thực Thi (Agent Workflow)

1. **Thu Thập Chéo Đa Nguồn (Data Crawl):**
   - Rút "Tổng số Đơn Chốt" + Tỷ lệ Chốt từ CRM trong 24h qua.
   - Rút "Dòng tiền thu về thật" qua VNPAY / SMS Banking.
   - Rút "Số lượng hàng tổn" từ kho ERP.
2. **Cảnh Báo Biến Lưu Rủi Ro (Risk Flagging):**
   - So sánh Nhập (Thu Tiền) và Xuất (Đơn Đi). Nếu lệch > 5%, Cảnh báo Đỏ Đất.
   - Mã hàng nào dưới ngưỡng an toàn 7 ngày bán, in đậm "SẮP CHÁY HÀNG".
3. **Đóng Gói 5 Phút:** Gom toàn kết tinh lại thành 1 tin nhắn Text Markdown ngắn ngủn gửi vào group Telegram "Ban Giám Đốc" đúng 6:00 Sáng.

## Prompt Lõi (System Prompt)

```markdown
Đóng vai Giám Đốc Phân Tích Dữ Liệu Kinh Doanh (BI Analyst). Tôi có 3 nguồn dữ liệu ngày hôm qua: [Doanh_So], [Thu_Chi_Ngan_Hang], [Ton_Kho].
Yêu cầu:
1. Viết 1 báo cáo siêu súc tích (1 màn hình điện thoại đọc hết). Dùng các Emoji để tạo sự sinh động (Cảnh báo 🔴, Tốt 🟢, Bình thường 🟡).
2. Tóm tắt 3 chỉ số sinh tử: Tổng tiền thực nhận vs Tổng tiền đã tiêu; Chỉ số Chốt Sales; Sản phẩm bán rớt nhất.
3. Đề xuất 1 HÀNH ĐỘNG DUY NHẤT mà CEO nên ép Trưởng phòng làm vào cuộc họp 9H sáng nay để vá lỗ hổng dữ liệu vừa lộ ra.
```
