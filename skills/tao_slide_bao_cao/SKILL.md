---
name: Tạo Slide Báo Cáo Tự Động (Auto Report Presentation)
description: Đọc dữ liệu từ file Excel/CSV, tự động tạo slide PowerPoint chuyên nghiệp với biểu đồ, bảng số liệu và insight tóm tắt.
---

# Skill: Tạo Slide Báo Cáo Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Trưởng phòng/Manager cần:

- Chuẩn bị slide báo cáo tuần/tháng/quý cho cuộc họp Ban Giám đốc
- Chuyển đổi từ bảng Excel nhàm chán thành slide trực quan trong 1 phút
- Tạo slide thuyết trình cho khách hàng/đối tác

## Tại Sao SME Cần Skill Này?

Mỗi thứ Hai, 5 trưởng phòng mỗi người mất 2-3 giờ "Cắt bảng Excel → Paste vào PowerPoint → Chỉnh font → Vẽ biểu đồ → Thêm title." Tổng cộng 15 giờ/tuần cho việc... copy-paste có kỹ thuật. Chất lượng slide thì mỗi người mỗi kiểu, CEO nhìn muốn đau mắt.

## Nguyên Liệu Đầu Vào

- **File dữ liệu:** Excel/CSV chứa số liệu cần trình bày.
- **Template (Tùy chọn):** File `.pptx` mẫu có sẵn logo, màu sắc thương hiệu.
- **Yêu cầu:** Số slide cần tạo, nội dung mỗi slide (tóm tắt, biểu đồ, bảng...).

## Quy Trình Thực Hiện

### Bước 1: Phân Tích Dữ Liệu

- Đọc file dữ liệu nguồn bằng Pandas.
- Tự động xác định các KPI chính (Doanh thu, Chi phí, % Tăng trưởng...).
- Tính toán các insight: Top 3 tốt nhất, Bottom 3 kém nhất, Trend tăng/giảm.

### Bước 2: Thiết Kế Cấu Trúc Slide

Tạo bộ slide theo framework chuẩn:

| Slide # | Nội dung | Loại |
| :--- | :--- | :--- |
| 1 | Title + Tên báo cáo + Kỳ báo cáo | Title Slide |
| 2 | Tóm tắt 3-5 KPI chính (số lớn, bold) | KPI Dashboard |
| 3 | Biểu đồ cột Doanh Thu theo tháng/chi nhánh | Chart Slide |
| 4 | Biểu đồ tròn Cơ cấu Chi phí | Chart Slide |
| 5 | Bảng Top 5 Sản phẩm bán chạy | Table Slide |
| 6 | 3 Insight chính + Đề xuất hành động | Bullet Points |

### Bước 3: Tạo PowerPoint

- Dùng thư viện `python-pptx` để tạo file `.pptx`.
- Áp dụng template (nếu có) hoặc dùng theme mặc định đẹp.
- Nhúng biểu đồ Matplotlib/Plotly dưới dạng ảnh vào slide.
- Format: Font tiếng Việt (Arial/Roboto), màu sắc nhất quán, logo công ty.

### Bước 4: Xuất File

- Lưu `BaoCao_Thang_X.pptx` tại thư mục output.
- Báo cáo cho người dùng: "Đã tạo 6 slide, gồm 2 biểu đồ và 1 bảng số liệu."

## Ví Dụ Prompt Gọi Skill

```
"Tạo slide báo cáo tháng 8 cho cuộc họp Ban Giám đốc thứ Hai tuần sau.
Dữ liệu: `/BaoCao/DoanhThu_T8.xlsx` và `/BaoCao/ChiPhi_T8.xlsx`.
Tạo 6 slides: Title, KPI tổng quan, biểu đồ doanh thu theo chi nhánh,
biểu đồ chi phí, bảng top 5 SP, và slide đề xuất.
Dùng màu xanh navy làm chủ đạo. Lưu file `/Output/BaoCao_T8.pptx`."
```

## Lưu Ý

- Slide tạo tự động là bản nháp. Trưởng phòng nên review trước khi trình bày.
- Nếu dữ liệu quá nhiều cột, AI sẽ tự chọn 5-7 cột quan trọng nhất để trình bày.
- Hỗ trợ tiếng Việt có dấu đầy đủ trong slide.
