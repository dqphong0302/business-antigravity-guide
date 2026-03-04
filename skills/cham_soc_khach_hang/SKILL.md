---
name: Chăm Sóc Khách Hàng Tự Động (Auto Customer Care)
description: Đọc lịch sử mua hàng, phân loại khách VIP/Thường/Rời bỏ, tự động gửi tin nhắn chăm sóc cá nhân hóa theo từng phân khúc.
---

# Skill: Hệ Thống Chăm Sóc Khách Hàng Tự Động (CRM Lite)

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Sales/Marketing/CSKH cần:

- Phân loại khách hàng theo giá trị (RFM Analysis)
- Tìm khách hàng đang "Rời bỏ" (Churn) để giữ chân kịp thời
- Gửi tin nhắn/email chăm sóc cá nhân hóa theo từng nhóm

## Tại Sao SME Cần Skill Này?

Công ty có 5,000 khách hàng trong file Excel. Không ai biết ai là khách VIP (mua nhiều, thường xuyên), ai là khách "Zombie" (mua 1 lần rồi biến mất). Marketing gửi SMS giống nhau cho tất cả → Khách VIP thấy bị coi thường, khách mới thấy spam. Tỷ lệ mở tin < 2%.

## Nguyên Liệu Đầu Vào

- **File lịch sử mua hàng:** Excel/CSV (cột: Mã KH, Tên, SĐT/Email, Ngày mua, Sản phẩm, Số tiền).
- **File template tin nhắn:** Mẫu SMS/Email cho từng phân khúc.

## Quy Trình Thực Hiện

### Bước 1: Phân Tích RFM (Recency - Frequency - Monetary)

Đây là mô hình phân loại khách hàng chuẩn quốc tế:

| Chỉ số | Ý nghĩa | Cách tính |
| :--- | :--- | :--- |
| **R** (Recency) | Mua gần đây không? | Số ngày từ lần mua cuối đến hôm nay |
| **F** (Frequency) | Mua thường xuyên không? | Tổng số lần mua hàng |
| **M** (Monetary) | Chi nhiều tiền không? | Tổng số tiền đã chi |

- Gán điểm 1-5 cho mỗi chỉ số (5 = tốt nhất).
- Ví dụ: Khách có R=5, F=5, M=5 → Khách VIP Vàng.

### Bước 2: Phân Khúc Khách Hàng (Segmentation)

| Phân khúc | Điều kiện RFM | Hành động đề xuất |
| :--- | :--- | :--- |
| 👑 **VIP Champions** | R≥4, F≥4, M≥4 | Gửi ưu đãi độc quyền, mời event |
| 💎 **Loyal** | F≥3, M≥3 | Tri ân, tặng voucher sinh nhật |
| 🌱 **Khách Mới Tiềm Năng** | R≥4, F=1 | Gửi hướng dẫn sử dụng, ưu đãi lần 2 |
| ⚠️ **Sắp Rời Bỏ** | R≤2, F≥2 | Gửi khảo sát "Vì sao anh/chị không quay lại?" |
| 💀 **Mất Khách** | R=1, F=1, M≤2 | Gửi deal "Come Back" giảm 30% |

### Bước 3: Cá Nhân Hóa Nội Dung

- Đọc template tin nhắn cho từng phân khúc.
- Thay thế biến: `{{TEN}}`, `{{SAN_PHAM_DA_MUA}}`, `{{NGAY_MUA_CUOI}}`, `{{UU_DAI}}`.
- Ví dụ template VIP: *"Chào anh {{TEN}}, cảm ơn anh đã đồng hành cùng [Tên Cty] suốt năm qua! Tặng anh voucher 500K cho đơn hàng tiếp theo. Mã: VIP{{MA_KH}}"*

### Bước 4: Xuất Kết Quả

- **File `PhanLoai_KhachHang.xlsx`:**
  - Sheet 1: Bảng RFM đầy đủ (5,000 dòng) với cột Phân Khúc.
  - Sheet 2: Dashboard tóm tắt: Bao nhiêu VIP, bao nhiêu Sắp Rời, Tổng giá trị mỗi nhóm.
- **File `DanhSach_GuiTin_Tung_Nhom/`:** 5 file CSV, mỗi file là 1 phân khúc sẵn sàng import vào tool gửi SMS/Email.
- Biểu đồ tròn: Tỷ lệ phân bổ khách hàng theo phân khúc.

## Ví Dụ Prompt Gọi Skill

```
"Antigravity, đọc file `/KhachHang/LichSuMuaHang_2024.xlsx`. 
Chạy phân tích RFM. Chia khách thành 5 nhóm. 
Xuất danh sách khách Sắp Rời Bỏ (At Risk) riêng 1 file CSV.
Với nhóm VIP, tạo nội dung SMS cá nhân hóa chúc Tết kèm voucher 500K.
Báo cáo: Bao nhiêu khách VIP, bao nhiêu khách mất, tổng giá trị từng nhóm."
```

## Lưu Ý

- Tuân thủ Luật bảo vệ dữ liệu cá nhân (PDPA). Không phát tán SĐT/Email.
- Giới hạn gửi SMS/Email theo quy định nhà cung cấp (tránh bị đánh Spam).
- RFM chỉ là điểm khởi đầu. Kết hợp với Skill `phan_tich_review` để hiểu WHY khách rời bỏ.
