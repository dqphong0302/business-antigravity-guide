---
name: Phân Tích Báo Cáo Tài Chính (Financial Deep Dive)
description: Đọc song song nhiều file PDF Báo cáo tài chính, trích xuất dữ liệu mấu chốt, phân tích sức khỏe tài chính và so sánh rủi ro (Nợ vay, Biên lợi nhuận, Dòng tiền).
---

# Skill: Phân Tích Báo Cáo Tài Chính (Financial Forensic)

## Bối Cảnh Sử Dụng

Việc đọc Báo cáo tài chính (BCTC) dài 150 trang là nỗi ám ảnh của nhà đầu tư tay ngang. Skill này dùng AI (OCR và RAG) để "nuốt trọn" BCTC trong 10 giây, tìm ra các thông số cốt lõi ẩn giấu ở phần Thuyết minh, và vạch trần các rủi ro "xào nấu" sổ sách.

## Nguyên Liệu Đầu Vào

- File PDF BCTC Hợp nhất (Quý hoặc Năm) của công ty mục tiêu.
- Thư mục chuẩn: `/Chung_Khoan/BCTC/`.

## Quy Trình Thực Hiện

### Bước 1: Trích Xuất Dữ Liệu (OCR & Semantic Search)

- Đọc nội dung file PDF. Chỉ quét các Bảng Cân đối Kế toán, Báo cáo KQKD, và Báo cáo Lưu chuyển Tiền tệ.
- Tìm chuẩn các số liệu: Doanh thu thuần, Lợi nhuận gộp, Nợ ngắn/dài hạn, Hàng tồn kho, Khoản phải thu.

### Bước 2: Chẩn Đoán Sức Khỏe (Financial Diagnosis)

AI sẽ tính toán hàng loạt chỉ số tự động:

- **Biên lợi nhuận:** Có tăng đều không? (Nếu Doanh thu tăng mà Lợi nhuận giảm → Báo Động).
- **Chất lượng Tài sản:** "Khoản phải thu" có phình to bất thường không? (Rủi ro ghi nhận doanh thu ảo).
- **Dòng tiền (Cashflow):** Lợi nhuận kỷ lục nhưng Dòng tiền kinh doanh âm nặng → Lãi giả, tiền chưa thu được.

### Bước 3: Đóng Gói Phân Tích & Chấm Điểm

- Tạo Bảng Cân Đối Tóm Tắt (Executive Summary).
- Đưa ra mục `Red Flags` (Còi Hú Đỏ): Chỉ ra những điểm mù rủi ro.
- Xuất file báo cáo Markdown hoặc PDF cực kỳ sắc nét.

## Ví Dụ Prompt Gọi Skill

```
"Vào thư mục /Chung_Khoan/BCTC/ đọc file HPG_Q3.pdf và HSG_Q3.pdf.
Hãy so sánh biên lợi nhuận gộp của 2 công ty này. Xem xét Hàng tồn kho của ai 
đang phình to nhanh hơn. Viết cho tôi một bản phân tích 5 ý chính (Bullet points) 
chỉ ra doanh nghiệp nào đang an toàn hơn để nắm giữ dài hạn."
```
