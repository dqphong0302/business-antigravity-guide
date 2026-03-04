---
description: Dịch thuật tài liệu đa ngôn ngữ và kiểm tra chất lượng bản dịch (Tổng hợp)
---

# Dịch Thuật Tài Liệu Tự Động

// turbo-all

Quy trình dịch thuật:

1. Đọc file tài liệu gốc tại đường dẫn được chỉ định (PDF/DOCX/TXT).
2. Nếu là PDF: dùng `pdfplumber` trích xuất text trước.
3. Chia văn bản thành các đoạn nhỏ (mỗi đoạn ~500 từ) để dịch chính xác hơn.
4. Dịch từng đoạn sang ngôn ngữ đích (mặc định: Tiếng Việt ↔ Tiếng Anh).
5. Giữ nguyên: Tên riêng, Số liệu, Thuật ngữ kỹ thuật (in nghiêng gốc bên cạnh).
6. Gộp kết quả thành file `[tên_gốc]_Dich_[Ngon_Ngu].docx`.
7. Tạo bảng so sánh song ngữ (cột trái: gốc, cột phải: bản dịch) trong Sheet Excel phụ.
8. In tóm tắt: Số trang, Số từ, Ngôn ngữ nguồn → đích.
