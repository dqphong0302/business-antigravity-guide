---
name: Quản Lý Hợp Đồng (Contract Management)
description: Quét thư mục chứa hợp đồng PDF/DOCX, trích xuất thông tin chủ chốt (bên ký, giá trị, ngày hết hạn), cảnh báo hợp đồng sắp hết hạn và xuất bảng tổng hợp.
---

# Skill: Quản Lý & Cảnh Báo Hợp Đồng Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi CEO/Admin/Pháp chế cần:

- Rà soát toàn bộ hợp đồng đang có hiệu lực
- Tìm hợp đồng sắp hết hạn trong 30/60/90 ngày tới
- Tổng hợp giá trị hợp đồng theo đối tác hoặc theo năm

## Tại Sao SME Cần Skill Này?

Công ty có 200 hợp đồng với nhà cung cấp, khách hàng, nhân sự. File nằm rải rác trong 5 thư mục, một số scan PDF mờ nhòe, một số Word do luật sư gửi. Không ai nhớ hợp đồng nào hết hạn tháng này. Khi phát hiện thì đã quá hạn 2 tuần, đối tác tự động gia hạn với giá cao hơn 15%.

## Nguyên Liệu Đầu Vào

- **Thư mục hợp đồng:** Chứa file PDF/DOCX (có thể lồng sub-folder theo năm/đối tác).
- **Ngưỡng cảnh báo:** Số ngày trước khi hết hạn cần cảnh báo (mặc định: 30 ngày).

## Quy Trình Thực Hiện

### Bước 1: Quét & Trích Xuất Text

- Duyệt đệ quy (recursive) tất cả file trong thư mục hợp đồng.
- PDF → dùng `pdfplumber` extract text.
- DOCX → dùng `python-docx` extract text.
- Lưu: {đường_dẫn_file, nội_dung_text, ngày_tạo_file}.

### Bước 2: Trích Xuất Thông Tin Chủ Chốt (Key Fields)

Dùng AI đọc hiểu ngữ nghĩa (NLP) kết hợp Regex để rút ra:

| Trường | Pattern tìm kiếm | Ví dụ |
| :--- | :--- | :--- |
| Bên A (Công ty mình) | Sau cụm "BÊN A:" hoặc "Party A:" | Công ty TNHH ABC |
| Bên B (Đối tác) | Sau cụm "BÊN B:" hoặc "Party B:" | Công ty CP XYZ |
| Giá trị hợp đồng | Regex số tiền VNĐ/USD gần cụm "giá trị" | 500,000,000 VNĐ |
| Ngày ký | Regex date gần cụm "ngày ký" | 15/03/2024 |
| Ngày hết hạn | Regex date gần cụm "hết hạn", "hiệu lực đến" | 15/03/2025 |
| Loại hợp đồng | Keywords: "thuê", "mua bán", "dịch vụ", "lao động" | Hợp đồng dịch vụ |

### Bước 3: Phân Tích & Cảnh Báo

- Tính số ngày còn lại = Ngày hết hạn - Ngày hôm nay.
- Phân loại:
  - 🔴 **Khẩn cấp:** Còn ≤ 30 ngày hoặc đã quá hạn.
  - 🟡 **Chú ý:** Còn 31-90 ngày.
  - 🟢 **An toàn:** Còn > 90 ngày.
- Tính tổng giá trị hợp đồng theo Đối tác và theo Loại.

### Bước 4: Xuất Báo Cáo

- Tạo file `BaoCao_HopDong.xlsx` gồm:
  - **Sheet 1 "Tổng Quan":** Bảng tất cả hợp đồng, sắp xếp theo ngày hết hạn tăng dần. Tô màu theo mức cảnh báo.
  - **Sheet 2 "Sắp Hết Hạn":** Chỉ các HĐ 🔴🟡, kèm link file gốc.
  - **Sheet 3 "Thống Kê":** Tổng giá trị theo đối tác, biểu đồ tròn theo loại HĐ.
- Gửi cảnh báo cho người dùng: Danh sách HĐ sắp hết hạn + đề xuất hành động.

### Bước 5 (Tùy chọn): Tự Động Nhắc Lịch

- Tạo file Cronjob chạy Skill này mỗi thứ Hai đầu tuần.
- Nếu phát hiện HĐ 🔴 → Gửi Telegram/Email cho CEO ngay lập tức.

## Ví Dụ Prompt Gọi Skill

```
"Antigravity, quét thư mục `/HopDong/` của tôi. Trích xuất Bên ký, Giá trị, 
Ngày hết hạn từ tất cả file PDF/Word. Cảnh báo hợp đồng nào hết hạn trong 
60 ngày tới. Xuất file Excel có tô màu cảnh báo. Liệt kê top 5 đối tác 
có tổng giá trị hợp đồng lớn nhất."
```

## Lưu Ý Quan Trọng

- Hợp đồng là tài liệu MẬT. Không gửi nội dung ra bên ngoài.
- Nếu file PDF bị scan mờ không đọc được ngày, ghi vào danh sách "Cần Kiểm Tra Thủ Công".
- Không tự ý gia hạn hoặc hủy hợp đồng. Chỉ CẢNH BÁO cho con người quyết định.
