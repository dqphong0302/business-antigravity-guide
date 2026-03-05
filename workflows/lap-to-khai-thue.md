---
description: "Tự động Lập tờ khai thuế GTGT hàng tháng từ bảng kê excel"
---

# Lệnh: `/lap-to-khai-thue`

**Phòng ban:** Kế Toán & Tài Chính

## Kịch Bản Luồng Chạy (Workflow Execution)

1. Tự động tìm kiếm file `bang_ke_ban_ra.xlsx` và `bang_ke_mua_vao.xlsx` trong thư mục quy định.
// turbo
2. Đọc và lấy tổng doanh thu chưa thuế, tổng thuế đầu ra, đầu vào.
// turbo
3. Đẩy dữ liệu qua kỹ năng OCR/Xử lý bảng tính của Antigravity (Skill: `lap_to_khai_thue`).
// turbo
4. Tạo Bảng Tóm Tắt Tờ Khai định dạng Markdown và xuất file PDF lưu vào `/Report/Thue/`
// turbo
5. Gửi thông báo đến Zalo/Slack của Kế toán trưởng để chờ duyệt nộp HTKK.
