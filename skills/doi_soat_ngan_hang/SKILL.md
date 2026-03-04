---
name: Đối Soát Ngân Hàng (Bank Reconciliation)
description: Tự động đọc 2 file (Sổ kế toán nội bộ + Sao kê Ngân hàng), đối chiếu chéo theo Mã Giao Dịch, xuất báo cáo chênh lệch có tô màu đỏ.
---

# Skill: Đối Soát Ngân Hàng Tự Động

## Bối Cảnh Sử Dụng

Skill này được kích hoạt khi người dùng yêu cầu so sánh, đối chiếu, hoặc reconcile giữa 2 nguồn dữ liệu tài chính (file Excel, CSV). Thường dùng vào cuối tháng khi Kế toán cần kiểm tra tiền vào/ra.

## Nguyên Liệu Đầu Vào

- **File A:** Sổ kế toán nội bộ (Excel/CSV) chứa các cột: `Ngày`, `Mã Giao Dịch`, `Số Tiền`, `Diễn Giải`.
- **File B:** Sao kê ngân hàng (Excel/CSV) chứa các cột tương tự nhưng có thể đặt tên khác.
- Người dùng sẽ chỉ định đường dẫn 2 file và tên cột dùng để đối chiếu (Key Column).

## Quy Trình Thực Hiện

### Bước 1: Đọc & Chuẩn Hóa Dữ Liệu

- Dùng `run_command` chạy Python script với thư viện Pandas.
- Đọc cả 2 file bằng `pd.read_excel()` hoặc `pd.read_csv()`.
- Chuẩn hóa: Trim khoảng trắng, uppercase cột Key, chuyển cột Số Tiền về dạng số (loại bỏ ký tự "VNĐ", dấu phẩy).

### Bước 2: Đối Chiếu Chéo (Cross-Match)

- Dùng `pd.merge()` với `how='outer'` và `indicator=True`.
- Phân loại kết quả:
  1. **Chỉ có ở Sổ Nội Bộ** (`left_only`): Giao dịch ghi sổ nhưng ngân hàng chưa xác nhận.
  2. **Chỉ có ở Sao kê NH** (`right_only`): Tiền vào/ra mà kế toán chưa ghi nhận.
  3. **Có ở cả hai nhưng Số Tiền lệch**: So sánh cột tiền, lọc ra các dòng chênh lệch > 0đ.

### Bước 3: Xuất Báo Cáo Excel Có Highlight

- Dùng thư viện `openpyxl` để tạo file Excel với 3 Sheet:
  - Sheet 1: "Thiếu Ghi Nhận" (left_only)
  - Sheet 2: "Tiền Không Nguồn" (right_only)  
  - Sheet 3: "Lệch Số Tiền" (chênh lệch)
- Tô nền đỏ (`PatternFill(fgColor='FF0000')`) cho các ô Số Tiền bị lệch.
- Lưu file tại đường dẫn người dùng chỉ định hoặc mặc định `/Output/BaoCao_DoiSoat.xlsx`.

### Bước 4: Báo Cáo Kết Quả

- Dùng `notify_user` thông báo:
  - Tổng số giao dịch đã quét.
  - Số giao dịch khớp hoàn hảo.
  - Số giao dịch có vấn đề (chia theo 3 loại).
  - Đường dẫn file báo cáo.

## Lưu Ý Quan Trọng

- TUYỆT ĐỐI KHÔNG xóa hoặc sửa file dữ liệu gốc.
- Nếu cột Key không tìm thấy trong file, dừng lại và hỏi người dùng tên cột chính xác.
- Nếu file quá lớn (>100MB), cảnh báo người dùng về thời gian xử lý.
