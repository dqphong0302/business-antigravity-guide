---
description: Trích xuất hóa đơn PDF tự động và lập bảng kê thuế VAT (Kế toán)
---

# Trích Xuất Hóa Đơn & Lập Bảng Kê VAT

// turbo-all

Quy trình xử lý hóa đơn đầu vào:

1. Quét thư mục `/KeToan/HoaDon_DauVao/` tìm tất cả file PDF.
2. Với mỗi file PDF: Dùng thư viện `pdfplumber` trích xuất text. Tìm các trường: Mã Số Thuế, Tên Nhà Cung Cấp, Tiền Hàng, Thuế VAT (%), Số Tiền VAT, Ngày Hóa Đơn.
3. Nếu file PDF không có text layer (scan ảnh): Di chuyển vào `/KeToan/HoaDon_CanCheckTay/` và ghi log.
4. Gộp tất cả dữ liệu đã trích xuất thành bảng Excel `Bang_Ke_Mua_Vao_ThangX.xlsx`.
5. Sheet 1: Bảng kê chi tiết (1 dòng = 1 hóa đơn).
6. Sheet 2: Tổng hợp theo Mã Số Thuế (gộp nhóm nhà cung cấp).
7. Sheet 3: Danh sách file lỗi + lý do (nếu có).
8. In tóm tắt: Tổng số hóa đơn đã xử lý, số file lỗi, tổng tiền hàng + VAT.
