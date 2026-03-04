---
description: Che giấu dữ liệu nhạy cảm trước khi phân tích (Bảo mật / IT)
---

# Data Masking — Che Giấu Dữ Liệu Nhạy Cảm

// turbo-all

Quy trình bảo mật dữ liệu trước khi phân tích:

1. Đọc file dữ liệu gốc tại đường dẫn được chỉ định (Excel/CSV).
2. Quét tất cả tên cột. Tự động phát hiện cột nhạy cảm theo pattern:
   - Chứa từ: "CCCD", "CMND", "the_tin_dung", "credit_card", "so_tai_khoan"
   - Chứa từ: "ho_ten", "ten_nhan_vien", "full_name"
   - Chứa từ: "luong", "salary", "thu_nhap", "income"
   - Chứa từ: "mat_khau", "password", "api_key", "token"
3. Thay toàn bộ giá trị trong các cột nhạy cảm bằng `***[DA_AN_GIẤU]***`.
4. Lưu file kết quả: `[tên_gốc]_SAFE_DRAFT.csv` tại cùng thư mục.
5. In danh sách cột đã masking và số dòng đã xử lý.
6. CẢNH BÁO: Sau bước này, mọi phân tích tiếp theo CHỈ ĐƯỢC thực hiện trên file `_SAFE_DRAFT`. Cấm truy cập file gốc.
