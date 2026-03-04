---
name: Trích Xuất Hóa Đơn PDF (Invoice OCR Extraction)
description: Đọc hàng loạt file PDF hóa đơn, trích xuất Mã số thuế, Số tiền, Thuế GTGT bằng Regex, và xuất bảng kê khai mua vào/bán ra.
---

# Skill: Trích Xuất Hóa Đơn Hàng Loạt

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Kế toán yêu cầu xử lý, trích xuất, hoặc tổng hợp thông tin từ nhiều file hóa đơn PDF. Thường dùng cho kê khai thuế VAT cuối kỳ.

## Quy Trình Thực Hiện

1. Quét thư mục chứa hóa đơn PDF bằng `list_dir`.
2. Dùng `pdfplumber` extract text từ từng file.
3. Dùng Regex trích xuất: Mã số thuế (`\d{10,13}`), Cộng tiền hàng, Tiền thuế GTGT.
4. Gom tất cả vào DataFrame Pandas, xuất file `Bang_Ke_Hoa_Don.xlsx`.
5. File nào lỗi đọc → Ghi vào Sheet riêng "Hoa_Don_Loi".

## Lưu Ý

- Không sửa file PDF gốc. Không tự đoán MST nếu không đọc được.
