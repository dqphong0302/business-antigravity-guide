---
name: Phân Tích Hỗ Trợ Ra Quyết Định (Decision Support Analysis)
description: Đọc dữ liệu lịch sử kinh doanh, chạy mô hình thống kê (Hồi quy, Mô phỏng), và đưa ra khuyến nghị có căn cứ số liệu cho các quyết định chiến lược.
---

# Skill: Hệ Thống Hỗ Trợ Ra Quyết Định (DSS)

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi CEO/CFO cần đánh giá rủi ro của một quyết định lớn: Tăng giá, Mở chi nhánh, Cắt ngân sách, Thay đổi nhà cung cấp. AI sẽ dựa trên dữ liệu lịch sử để mô phỏng kịch bản tương lai.

## Nguyên Liệu Đầu Vào

- **File dữ liệu lịch sử:** Excel/CSV chứa dữ liệu kinh doanh >=6 tháng.
- **Câu hỏi quyết định:** Mệnh đề cần đánh giá (ví dụ: "Nếu tăng giá 10%, doanh thu sẽ ra sao?").
- **Biến số cần phân tích:** Cột nào là Biến Độc lập (Giá), cột nào là Biến Phụ thuộc (Sản lượng/Doanh thu).

## Quy Trình Thực Hiện

### Bước 1: Làm Sạch & Khám Phá Dữ Liệu (EDA)

- Đọc file, kiểm tra tổng quan: số dòng, số cột, giá trị thiếu (null).
- Vẽ biểu đồ phân phối (Histogram) cho các biến quan trọng.
- Xác định xu hướng (Trend) và mùa vụ (Seasonality) nếu có.

### Bước 2: Xây Dựng Mô Hình Dự Báo

- Tùy theo bài toán, chọn 1 trong các mô hình:
  - **Hồi quy tuyến tính (Linear Regression):** Cho bài toán Giá vs Sản lượng.
  - **ARIMA/Prophet:** Cho bài toán dự báo theo chuỗi thời gian.
  - **Monte Carlo Simulation:** Cho bài toán đánh giá rủi ro với nhiều biến số.
- Chạy mô hình bằng Python (`statsmodels`, `scikit-learn`, hoặc `prophet`).

### Bước 3: Mô Phỏng Kịch Bản (Scenario Analysis)

- Dựa trên câu hỏi quyết định, tạo 3 kịch bản:
  1. **Lạc quan (Best Case):** Giả định điều kiện thuận lợi nhất.
  2. **Trung bình (Base Case):** Giả định mọi thứ như hiện tại.
  3. **Bi quan (Worst Case):** Giả định rủi ro xảy ra.
- Tính toán Doanh thu / Lợi nhuận dự kiến cho mỗi kịch bản.

### Bước 4: Trực Quan Hóa & Khuyến Nghị

- Vẽ biểu đồ đường (Line Chart) so sánh 3 kịch bản.
- Đưa ra khuyến nghị rõ ràng: NÊN hay KHÔNG NÊN thực hiện quyết định.
- Ghi rõ mức độ tin cậy (Confidence Level) và giới hạn của mô hình.

## Lưu Ý

- Luôn ghi disclaimer: "Đây là mô hình dự báo dựa trên dữ liệu quá khứ, không đảm bảo tương lai."
- Nếu dữ liệu ít hơn 3 tháng, cảnh báo kết quả không đáng tin cậy.
- Không tự động thực thi quyết định. Chỉ đưa khuyến nghị cho CON NGƯỜI ra quyết định cuối cùng.
