---
name: Phân Tích Lãi Lỗ Kinh Doanh (P&L Analysis)
description: Đọc dữ liệu Doanh thu và Chi phí từ nhiều nguồn file, tự động tính Lợi nhuận gộp/ròng, phân tích theo sản phẩm/chi nhánh, và xuất báo cáo P&L chuẩn kế toán.
---

# Skill: Phân Tích Báo Cáo Lãi Lỗ (Profit & Loss) Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi CEO/CFO cần:

- Biết công ty đang Lãi hay Lỗ trong tháng/quý vừa qua
- Phân tích sản phẩm/dịch vụ nào đang "Ngốn tiền" (lỗ) mà không ai biết
- So sánh P&L giữa các kỳ (tháng này vs tháng trước, quý này vs cùng kỳ năm trước)

## Tại Sao SME Cần Skill Này?

Đa số SME chỉ biết "Tháng này bán được bao nhiêu" nhưng KHÔNG biết "Tháng này LỜI được bao nhiêu" vì chi phí nằm rải rác: Tiền lương file HR, tiền điện file Admin, tiền hàng file Kế toán, tiền Ads file Marketing. Không ai gộp lại!

## Nguyên Liệu Đầu Vào

- **File Doanh thu:** Excel/CSV ghi nhận doanh số bán hàng (cột: Ngày, Sản phẩm, Số lượng, Đơn giá, Thành tiền).
- **File Chi phí:** Excel/CSV tổng hợp chi phí (cột: Ngày, Hạng mục, Số tiền, Phòng ban).
- **Kỳ phân tích:** Tháng/Quý/Năm cần báo cáo.

## Quy Trình Thực Hiện

### Bước 1: Thu Thập & Hợp Nhất Dữ Liệu

- Đọc tất cả file Doanh thu → Gộp thành DataFrame `df_revenue`.
- Đọc tất cả file Chi phí → Gộp thành DataFrame `df_cost`.
- Chuẩn hóa: Đồng nhất format ngày, loại bỏ dòng trùng, xử lý giá trị null.

### Bước 2: Tính Toán Các Chỉ Số P&L

```python
# Pseudo-code Tính P&L
Tong_Doanh_Thu = SUM(df_revenue['Thanh_Tien'])
Gia_Von_Hang_Ban (COGS) = SUM(df_cost[Loai == 'Nguyên vật liệu'])
Loi_Nhuan_Gop = Tong_Doanh_Thu - COGS
Margin_Gop = Loi_Nhuan_Gop / Tong_Doanh_Thu * 100

Chi_Phi_Van_Hanh = SUM(df_cost[Loai IN ('Lương', 'Điện', 'Thuê VP', 'Marketing')])
Chi_Phi_Khac = SUM(df_cost[Loai == 'Khác'])

Loi_Nhuan_Rong = Loi_Nhuan_Gop - Chi_Phi_Van_Hanh - Chi_Phi_Khac
Margin_Rong = Loi_Nhuan_Rong / Tong_Doanh_Thu * 100
```

### Bước 3: Phân Tích Chi Tiết

- **Theo sản phẩm:** SP nào margin cao nhất / thấp nhất?
- **Theo chi nhánh:** Chi nhánh nào đang lỗ?
- **Theo thời gian:** Trend lãi/lỗ 6 tháng gần nhất.
- **Theo hạng mục chi phí:** Chi phí nào đang "phình to" bất thường?

### Bước 4: Trực Quan Hóa

- Vẽ bảng P&L chuẩn kế toán (Waterfall Chart hoặc bảng dọc).
- Biểu đồ tròn phân bổ chi phí.
- Biểu đồ đường trend Lợi nhuận ròng 6 tháng.
- Highlight đỏ các mục chi phí tăng > 20% so với kỳ trước.

### Bước 5: Xuất Báo Cáo

- File `BaoCao_PnL_ThangX.xlsx`:
  - Sheet 1: Bảng P&L tổng quan
  - Sheet 2: Chi tiết theo sản phẩm
  - Sheet 3: Chi tiết theo chi nhánh
  - Sheet 4: So sánh kỳ trước
- Ảnh biểu đồ: `PnL_Chart.png`
- Tóm tắt 1 dòng cho CEO: "Tháng 8 lãi ròng 450 triệu (margin 12%), giảm 3% so T7. Chi phí Marketing tăng đột biến 45%."

## Ví Dụ Prompt Gọi Skill

```
"CFO đây. Đọc file `/TaiChinh/DoanhThu_T8.xlsx` và `/TaiChinh/ChiPhi_T8.xlsx`.
Tính Lợi nhuận gộp, Lợi nhuận ròng, Margin. Phân tích SP nào lãi nhất, 
SP nào lỗ. So sánh với tháng 7 (file `/TaiChinh/DoanhThu_T7.xlsx`). 
Vẽ biểu đồ Waterfall P&L. Xuất báo cáo Excel + ảnh biểu đồ. 
Tóm tắt 3 dòng cho tôi đọc nhanh."
```

## Lưu Ý

- Dữ liệu tài chính là TỐI MẬT. Không gửi ra ngoài, chỉ xử lý local.
- Nếu thiếu file Chi phí một hạng mục, ghi chú "Chưa có dữ liệu" thay vì bỏ trống.
- P&L chỉ mang tính quản trị nội bộ, không thay thế báo cáo tài chính kiểm toán.
