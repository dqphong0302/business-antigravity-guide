---
name: Báo Cáo Doanh Thu Tháng (Monthly Revenue Report)
description: Đọc tất cả file Excel doanh thu trong tháng, tổng hợp theo chi nhánh/sản phẩm, vẽ biểu đồ so sánh, và xuất báo cáo tóm tắt cho Sếp.
---

# Skill: Báo Cáo Doanh Thu Tháng Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi người dùng yêu cầu tạo báo cáo doanh thu, tổng hợp doanh số, hoặc phân tích hiệu suất kinh doanh theo kỳ.

## Nguyên Liệu Đầu Vào

- **Thư mục dữ liệu:** Chứa các file Excel/CSV ghi nhận doanh thu hàng ngày hoặc hàng tuần.
- **Tháng cần báo cáo:** Người dùng chỉ định (mặc định: tháng hiện tại).

## Quy Trình Thực Hiện

### Bước 1: Thu Thập Dữ Liệu

- Dùng `list_dir` quét thư mục dữ liệu.
- Lọc các file có ngày tạo/tên file thuộc tháng cần báo cáo.
- Đọc tất cả file bằng Pandas, gộp thành 1 DataFrame tổng.

### Bước 2: Phân Tích

- Nhóm theo `Chi Nhánh` hoặc `Sản Phẩm` → Tính Tổng, Trung Bình, Min, Max.
- So sánh với tháng trước (nếu có dữ liệu): Tính % Tăng/Giảm.
- Xác định Top 3 sản phẩm/chi nhánh Tốt nhất và Kém nhất.

### Bước 3: Trực Quan Hóa

- Vẽ biểu đồ cột (Bar Chart) so sánh doanh thu theo chi nhánh.
- Cột giảm >20% so tháng trước → Tô màu Đỏ cảnh báo.
- Cột tăng >20% → Tô màu Xanh lá.
- Lưu ảnh biểu đồ tại `/Output/bieu_do_doanh_thu_thangX.png`.

### Bước 4: Xuất Báo Cáo

- Tạo file `BaoCao_DoanhThu_ThangX.xlsx` gồm:
  - Sheet 1: Bảng tổng hợp chi tiết.
  - Sheet 2: Bảng so sánh tháng trước vs tháng này.
- Thông báo kết quả cho người dùng kèm ảnh biểu đồ.

## Lưu Ý

- Không sửa đổi file dữ liệu gốc.
- Nếu thiếu dữ liệu tháng trước để so sánh, bỏ qua phần so sánh và ghi chú.
