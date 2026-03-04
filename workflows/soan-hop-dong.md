---
description: Soạn và kiểm tra hợp đồng lao động mới (HR / Pháp chế)
---

# Soạn Hợp Đồng Lao Động

// turbo-all

Quy trình soạn hợp đồng:

1. Đọc template hợp đồng mẫu tại `/HR/Templates/Hop_Dong_Mau.docx`.
2. Đọc file thông tin nhân viên mới: `/HR/NhanVien_Moi.xlsx` (Họ Tên, CCCD, Địa chỉ, Chức vụ, Lương cơ bản, Ngày vào).
3. Với mỗi nhân viên: Thay thế các placeholder trong template (`{{HO_TEN}}`, `{{CCCD}}`, `{{CHUC_VU}}`, `{{LUONG}}`, `{{NGAY_VAO}}`).
4. Xuất file riêng cho mỗi nhân viên: `HopDong_[HoTen].docx`.
5. Tạo bảng tổng hợp `DanhSach_HopDong_CanKy.xlsx`: Tên | Chức vụ | Loại HĐ | File đính kèm.
6. In tóm tắt: Đã tạo X hợp đồng. Danh sách file tại `/HR/HopDong_Moi/`.
7. CẢNH BÁO: Hợp đồng cần Sếp ký tay. AI không thể thay thế chữ ký pháp lý.
