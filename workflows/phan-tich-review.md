---
description: Thu thập và phân tích đánh giá khách hàng trên các sàn TMĐT (Marketing)
---

# Phân Tích Review Khách Hàng

Workflow này KHÔNG dùng `// turbo-all` vì cần giám sát browser agent.

Quy trình thu thập đánh giá:

1. Kích hoạt `browser_subagent`. Truy cập link sản phẩm trên Shopee/Lazada/Tiki do Sếp cung cấp.
2. Cuộn trang xuống phần Đánh giá. Thu thập: Tên người review, Số sao, Nội dung review, Ngày.
3. Wait 3-5 giây giữa mỗi trang review (Anti-bot).
4. Cào tối đa 500 review hoặc đến hết trang.
5. Dùng Python phân tích Sentiment (tích cực/tiêu cực):
   - Từ khóa tiêu cực: "tệ", "hỏng", "chậm", "lỗi", "giao sai"
   - Từ khóa tích cực: "tốt", "đẹp", "nhanh", "rẻ", "ưng"
6. Xuất `PhanTich_Review.xlsx`:
   - Sheet 1: Toàn bộ review + cột Sentiment.
   - Sheet 2: Thống kê: % Tích cực, % Tiêu cực, Top 5 từ khóa phàn nàn.
7. Vẽ biểu đồ Pie Chart tỷ lệ Sentiment. Lưu ảnh PNG.
