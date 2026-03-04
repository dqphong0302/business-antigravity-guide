# 📚 Danh Mục Toàn Bộ Skills Dành Cho Doanh Nghiệp (Business Skills Catalog)

> **Hướng dẫn sử dụng:** Mỗi Skill là một thư mục riêng trong `/skills/`. Bên trong có file `SKILL.md` mô tả chi tiết quy trình AI thực hiện. Bạn có thể mở bất kỳ Skill nào để đọc cách hoạt động, hoặc copy sang dự án của mình để Antigravity tự động áp dụng.

---

## 🏦 Khối Kế Toán - Tài Chính

| # | Tên Skill | Thư mục | Mô tả ngắn |
|:--|:----------|:--------|:------------|
| 1 | **Đối Soát Ngân Hàng** | `skills/doi_soat_ngan_hang/` | So sánh Sổ kế toán vs Sao kê NH → Xuất báo cáo chênh lệch tô đỏ |
| 2 | **Trích Xuất Hóa Đơn PDF** | `skills/trich_xuat_hoa_don/` | OCR hàng loạt hóa đơn → Rút MST, Tiền hàng, Thuế VAT → Bảng kê khai |
| 3 | **Báo Cáo Doanh Thu Tháng** | `skills/bao_cao_doanh_thu/` | Gộp nhiều file Excel → Tổng hợp theo chi nhánh → Biểu đồ so sánh |

---

## 👥 Khối Nhân Sự (HR)

| # | Tên Skill | Thư mục | Mô tả ngắn |
|:--|:----------|:--------|:------------|
| 4 | **Lọc CV Ứng Viên (ATS)** | `skills/loc_cv_ung_vien/` | Quét 300 CV → Chấm điểm theo JD → Phân loại Đạt/Không Đạt |

---

## 📢 Khối Marketing - Kinh Doanh

| # | Tên Skill | Thư mục | Mô tả ngắn |
|:--|:----------|:--------|:------------|
| 5 | **Cào Giá Đối Thủ** | `skills/crawl_gia_doi_thu/` | Browser cào Shopee/Tiki → Thu thập giá → So sánh với giá mình |
| 6 | **Tạo Báo Giá Tự Động** | `skills/tao_bao_gia/` | Đọc danh mục SP + Chiết khấu → Xuất báo giá Excel đẹp |
| 7 | **Email Marketing Hàng Loạt** | `skills/email_marketing/` | Đọc DS khách hàng → Cá nhân hóa nội dung → Gửi email SMTP |
| 8 | **Phân Tích Review Khách Hàng** | `skills/phan_tich_review/` | Phân loại Tích cực/Tiêu cực → Word Cloud → Tìm vấn đề phổ biến |

---

## 🏭 Khối Vận Hành - Kho Bãi

| # | Tên Skill | Thư mục | Mô tả ngắn |
|:--|:----------|:--------|:------------|
| 9 | **Cảnh Báo Tồn Kho Thấp** | `skills/canh_bao_ton_kho/` | Quét tồn kho → Phát hiện hàng sắp hết → Gửi cảnh báo đặt hàng |

---

## 🎯 Khối Lãnh Đạo - Chiến Lược

| # | Tên Skill | Thư mục | Mô tả ngắn |
|:--|:----------|:--------|:------------|
| 10 | **Hỗ Trợ Ra Quyết Định (DSS)** | `skills/phan_tich_quyet_dinh/` | Chạy mô hình thống kê → Mô phỏng 3 kịch bản → Khuyến nghị cho CEO |
| 11 | **Dịch Thuật Tài Liệu** | `skills/dich_thuat_tai_lieu/` | Dịch hợp đồng/báo giá sang Anh/Nhật/Hàn → Giữ nguyên format |

---

## 🔧 Cách Sử Dụng

### Cách 1: Để Antigravity tự nhận diện

Chỉ cần đặt thư mục `skills/` trong dự án. Khi bạn hỏi AI câu liên quan (ví dụ: "Đối soát 2 file Excel"), AI sẽ tự tìm Skill phù hợp và áp dụng.

### Cách 2: Chỉ định trực tiếp

Nói rõ trong Prompt: *"Hãy dùng Skill `doi_soat_ngan_hang` để xử lý 2 file này cho tôi."*

### Cách 3: Tùy chỉnh cho công ty mình

Copy bất kỳ thư mục Skill nào, sửa file `SKILL.md` bên trong cho phù hợp với quy trình riêng của doanh nghiệp bạn (đổi tên cột, đổi thư mục lưu trữ, thêm bước gửi Telegram...).
