---
name: Lập Kế Hoạch Ngân Sách (Budget Planning & Tracking)
description: Đọc dữ liệu chi tiêu thực tế và ngân sách dự kiến, so sánh Budget vs Actual, cảnh báo vượt ngân sách theo phòng ban/hạng mục.
---

# Skill: Lập Kế Hoạch & Giám Sát Ngân Sách Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi CFO/Kế toán trưởng cần:

- So sánh chi tiêu thực tế vs ngân sách đã duyệt
- Phát hiện phòng ban nào đang "vượt rào" ngân sách
- Dự báo chi tiêu cuối năm dựa trên xu hướng hiện tại

## Tại Sao SME Cần Skill Này?

Đầu năm Sếp duyệt ngân sách Marketing 200 triệu/quý. Giữa quý, Marketing đã xài 180 triệu nhưng không ai biết (vì file chi tiêu nằm ở Kế toán, file kế hoạch nằm ở Marketing). Cuối quý vỡ trận, cắt ngân sách HR để bù → HR không tuyển được người → Sản xuất thiếu nhân lực.

## Nguyên Liệu Đầu Vào

- **File Ngân sách dự kiến:** Excel với cột: Phòng ban, Hạng mục, Ngân sách Quý (VNĐ).
- **File Chi tiêu thực tế:** Excel/CSV xuất từ phần mềm kế toán, cột: Ngày, Phòng ban, Hạng mục, Số tiền.

## Quy Trình Thực Hiện

### Bước 1: Đọc & Mapping Dữ Liệu

- Đọc file Ngân sách → DataFrame `df_budget`.
- Đọc file Chi tiêu → DataFrame `df_actual`.
- Mapping: Đồng bộ tên Phòng ban (ví dụ: "Phòng MKT" = "Marketing" = "Dept. Marketing").

### Bước 2: Tính Toán Variance (Chênh Lệch)

```python
# Pseudo-code
Cho_Moi_Phong_Ban:
    Budget = df_budget[Phong_Ban]['Ngan_Sach']
    Actual = SUM(df_actual[Phong_Ban]['So_Tien'])
    Variance = Budget - Actual        # Dương = Dư, Âm = Vượt
    Pct_Used = Actual / Budget * 100  # % đã sử dụng
    
    Neu Pct_Used > 90%:  Canh_Bao("🔴 Sắp hết ngân sách!")
    Neu Pct_Used > 100%: Canh_Bao("🚨 ĐÃ VƯỢT NGÂN SÁCH!")
```

### Bước 3: Dự Báo Cuối Kỳ (Forecast)

- Tính tốc độ chi tiêu trung bình/ngày cho mỗi phòng ban.
- Nhân với số ngày còn lại trong quý → Dự báo tổng chi tiêu cuối kỳ.
- So sánh Forecast vs Budget → Cảnh báo sớm nếu có nguy cơ vượt.

### Bước 4: Xuất Báo Cáo

- **File `Budget_vs_Actual_QX.xlsx`:**
  - Sheet 1: Bảng tổng hợp Budget vs Actual vs Variance theo Phòng ban.
  - Sheet 2: Chi tiết từng giao dịch chi tiêu.
  - Sheet 3: Forecast cuối kỳ.
- Biểu đồ: Thanh ngang (Horizontal Bar) so sánh Budget vs Actual, tô đỏ phòng ban vượt.
- Tóm tắt: "Quý 3, 2/5 phòng ban vượt ngân sách. Marketing vượt 15% (30 triệu). IT còn dư 40%."

## Ví Dụ Prompt Gọi Skill

```
"Đọc file `/NganSach/Budget_Q3_2025.xlsx` và `/NganSach/ChiTieu_Thuc_Te_Q3.csv`.
So sánh ngân sách vs thực tế theo từng phòng ban. Cảnh báo phòng nào đã dùng 
>80% ngân sách. Dự báo cuối quý 3 mỗi phòng sẽ chi bao nhiêu. 
Xuất Excel + biểu đồ so sánh. Tóm tắt 3 dòng cho CEO."
```

## Lưu Ý

- Ngân sách là số liệu nhạy cảm. Xử lý local, không gửi ra ngoài.
- Nếu file chi tiêu thiếu cột Phòng ban, hỏi người dùng cách phân bổ.
