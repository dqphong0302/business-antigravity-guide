---
name: Cào Giá Đối Thủ (Competitor Price Scraping)
description: Dùng Browser Subagent lướt web thương mại điện tử (Shopee, Tiki, Lazada), thu thập giá bán của đối thủ cạnh tranh, lưu vào file CSV để so sánh.
---

# Skill: Thu Thập Giá Đối Thủ Cạnh Tranh Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi người dùng yêu cầu theo dõi giá, so sánh giá, hoặc nghiên cứu thị trường trực tuyến. Phù hợp cho phòng Marketing và Kinh doanh.

## Nguyên Liệu Đầu Vào

- **URL mục tiêu:** Đường dẫn trang web cần cào (ví dụ: `https://shopee.vn/search?keyword=may_loc_nuoc`).
- **Số lượng trang:** Số trang cần lướt qua (mặc định: 3 trang).
- **Thông tin cần lấy:** Tên sản phẩm, Giá bán, Tên shop, Số lượt bán.

## Quy Trình Thực Hiện

### Bước 1: Khởi Chạy Trình Duyệt

- Kích hoạt `browser_subagent` với URL mục tiêu.
- Đợi trang tải hoàn tất (wait for page load).
- Nếu có popup/quảng cáo, đóng chúng lại.

### Bước 2: Thu Thập Dữ Liệu

- Cuộn trang từ từ (scroll slowly) để tải lazy-load content.
- Đọc từng Card sản phẩm trên trang:
  - Trích xuất Tên sản phẩm (thường ở thẻ h2 hoặc a.title).
  - Trích xuất Giá (thường ở thẻ span.price).
  - Trích xuất Tên shop và Lượt bán (nếu có).
- Chuyển sang trang tiếp theo, lặp lại cho đến hết số trang yêu cầu.

### Bước 3: Lưu Trữ Kết Quả

- Ghi tất cả dữ liệu vào file CSV: `Gia_Doi_Thu_[YYYY-MM-DD].csv`.
- Các cột: `STT`, `Tên Sản Phẩm`, `Giá (VNĐ)`, `Shop`, `Lượt Bán`, `URL`.

### Bước 4: Phân Tích Sơ Bộ

- Tính Giá trung bình thị trường cho từng loại sản phẩm.
- So sánh với giá bán hiện tại của công ty (nếu người dùng cung cấp).
- Báo cáo: Bao nhiêu sp của mình đang Đắt hơn / Rẻ hơn thị trường.

## Lưu Ý

- Tuân thủ robots.txt của website. Không cào quá 5 trang/phút để tránh bị chặn IP.
- Dữ liệu giá có thể thay đổi theo giờ, ghi rõ timestamp khi lưu.
- Không lưu trữ thông tin cá nhân người bán (chỉ lấy tên shop công khai).
