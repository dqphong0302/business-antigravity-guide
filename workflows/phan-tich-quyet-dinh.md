---
description: Phân tích rủi ro và mô phỏng kịch bản kinh doanh Monte Carlo (Ban Giám đốc)
---

# Phân Tích Quyết Định Kinh Doanh (Decision Support)

Workflow này KHÔNG dùng `// turbo-all` vì cần Sếp review kết quả trước khi hành động.

Quy trình hỗ trợ ra quyết định:

1. Đọc file dữ liệu lịch sử kinh doanh tại đường dẫn Sếp cung cấp.
2. **Agent 1 — Price Elasticity:** Chạy mô hình hồi quy OLS bằng Python. Tính hệ số co giãn nhu cầu theo giá (Elasticity). In kết quả rõ ràng: "Elasticity = -X.X → Tăng 1% giá, lượng bán giảm X.X%".
3. **Agent 2 — Monte Carlo Simulation:** Giả lập 10.000 kịch bản ngẫu nhiên. Cho ra: Xác suất Lãi vs Lỗ. Khoảng tin cậy 95%. Set `np.random.seed(42)` cho kết quả reproducible.
4. **Agent 3 — Visualizer:** Vẽ biểu đồ 2 đường cong (Revenue vs Volume) dùng Matplotlib. Lưu `Decision_Matrix.png`. Dùng `plt.savefig()` (không dùng `plt.show()`).
5. In khuyến nghị cuối cùng: **LÀM, CHỜ, HAY HỦY** + Lý do 1 câu dựa trên dữ liệu.
6. Luôn in Confidence Interval. Nếu CI quá rộng: ghi rõ "Dữ liệu chưa đủ tin cậy".
