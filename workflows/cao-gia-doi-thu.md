---
description: Quét và phân tích giá đối thủ cạnh tranh trên sàn TMĐT (Sales / Marketing)
---

# Cào Giá Đối Thủ Cạnh Tranh

Workflow này KHÔNG dùng `// turbo-all` vì cần giám sát browser agent.

Quy trình theo dõi giá đối thủ:

1. Kích hoạt `browser_subagent`. Truy cập sàn TMĐT (Shopee/Lazada/Tiki).
2. Tìm kiếm sản phẩm cạnh tranh theo tên sản phẩm hoặc keyword Sếp cung cấp.
3. Thu thập từ Top 20 kết quả: Tên Shop, Tên Sản Phẩm, Giá Bán, Số Lượng Đã Bán, Số Đánh Giá, URL.
4. Wait 5 giây giữa mỗi lần click (Anti-bot).
5. Xuất `BangGia_DoiThu.xlsx`:
   - Sheet 1: Bảng giá chi tiết từng đối thủ.
   - Sheet 2: So sánh với giá của công ty mình.
   - Tô XANH nếu mình rẻ hơn, TÔ ĐỎ nếu mình đắt hơn.
6. Vẽ biểu đồ Bar Chart so sánh giá. Lưu `GiaSoSanh.png`.
7. In nhận xét: "Giá mình ở vị trí thứ X/20. Chênh lệch trung bình: ±Y%."
