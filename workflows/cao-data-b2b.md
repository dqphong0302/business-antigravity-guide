---
description: Cào dữ liệu khách hàng B2B từ trang tuyển dụng (Sales)
---

# Cào Data Khách Hàng B2B

Lưu ý: Workflow này KHÔNG dùng `// turbo-all` vì cần giám sát chống bị chặn.

Quy trình cào data B2B:

1. Kích hoạt `browser_subagent`. Truy cập trang web tuyển dụng được chỉ định.
2. Tìm kiếm theo từ khóa: "Tuyển dụng IT" hoặc "System Admin" hoặc keyword do Sếp chỉ định.
3. Với mỗi tin đăng tuyển:
   - Click vào bài đăng. Đọc tên công ty, quy mô nhân sự.
   - Tìm email (pattern có @) và SĐT liên hệ.
   - CHỜ 5-10 GIÂY giữa mỗi lần click (tránh chặn bot).
4. Ghi dữ liệu vào file `DanhSach_B2B.csv`: Tên Công Ty | Quy Mô | Email | SĐT | URL Gốc.
5. Khi cào xong 50 công ty, in tiến độ ra Terminal.
6. Nếu gặp CAPTCHA → Dừng lại, thông báo cho người dùng xử lý thủ công.
7. Mục tiêu: Cào hết các trang kết quả (phân trang Pagination). Dừng khi hết trang hoặc đạt số lượng Sếp chỉ định.
