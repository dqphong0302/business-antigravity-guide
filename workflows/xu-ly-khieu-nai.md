---
description: "Soạn thư xin lỗi Khách hàng có đính kèm Voucher ngay khi có Ticket Nhạy cảm"
---

# Lệnh: `/xu-ly-khieu-nai`

**Phòng ban:** Chăm Sóc Khách Hàng (CS)

## Kịch Bản Luồng Chạy (Workflow Execution)

1. Tự động gom Email/Ticket gửi tới phòng ban CSKH có Sentiment Score > 7 (Thái độ Cộc cằn/Chửi Bới).
// turbo
2. Cảnh báo cho Leader CSKH bằng 1 lệnh Ping Slack đỏ quạch.
// turbo
3. Đẩy nội dung khiếu nại qua module AI Phân tích Ngữ nghĩa `xu_ly_khieu_nai`.
// turbo
4. Soạn 1 Draft Thư (Email/Facebook Message) làm Mềm lòng khách hàng, đính kèm 1 file Voucher 20% cá nhân hóa.
// turbo
5. Nếu Sếp CSKH không phản hồi trong 1 tiếng, Draft tự động bị Xóa (Cần Human-in-The-Loop).
