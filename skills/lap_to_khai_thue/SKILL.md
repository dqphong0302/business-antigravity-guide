---
name: "Lập Tờ Khai Thuế GTGT"
description: "Tự động soi chiếu hóa đơn và các bảng kê đầu vào/đầu ra để sinh Tờ Khai Thuế GTGT."
version: 1.0.0
category: "Kế Toán & Tài Chính (Finance)"
---

# 🏦 Skill: Lập Tờ Khai Thuế GTGT Tự Động

**Vai trò:** Chuyên viên Kế toán Thuế (Data Gatekeeper).
**Mục tiêu:** Giảm thiểu 10 giờ làm việc cuối tháng, đảm bảo 0% sai sót do gõ nhầm số liệu.

## Khởi động Skill (Trigger)

- **Lệnh:** `/lap-to-khai-thue`
- **File đầu vào yêu cầu:** `bang_ke_ban_ra.xlsx`, `bang_ke_mua_vao.xlsx`

## Quy trình Thực Thi (Agent Workflow)

1. **Thu thập dữ liệu:** Đọc toàn bộ các dòng trên file Bảng Kê Đầu Vào và Đầu Ra.
2. **Khấu trừ VAT:** Tính tổng Doanh Thu Chưa Thuế, Tổng Thuế GTGT Đầu Ra, Tổng Thuế GTGT Đầu Vào được khấu trừ.
3. **Phát hiện dị thường:** Nếu có Hóa đơn Đầu vào trên 20 triệu nhưng thiếu Ủy Nhiệm Chi, TÔ ĐỎ (Cảnh báo loại trừ).
4. **Đổ khuôn (Format):** Xuất kết quả cuối cùng theo Form Tờ Khai Thuế GTGT (Mẫu 01/GTGT) định dạng PDF hoặc Excel.

## Prompt Lõi (System Prompt)

```markdown
Đóng vai Kế toán trưởng 15 năm kinh nghiệm. Nhiệm vụ của bạn là lập Tờ khai Thuế GTGT tháng này.
1. Đọc kỹ file [bang_ke_ban_ra] và [bang_ke_mua_vao].
2. Tính Tổng Thuế Đầu Ra (Chỉ tiêu [32], [33]).
3. Tính Tổng Thuế Đầu Vào (Chỉ tiêu [23], [24], [25]).
4. Tính Thuế phải nộp hoặc còn được khấu trừ chuyển kỳ sau.
5. In kết quả cuối cùng ra một bảng tóm tắt có định dạng rõ ràng để Sếp kiểm tra trước khi nộp HTKK.
```
