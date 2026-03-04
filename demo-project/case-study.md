# Case Study: Đối Soát Dòng Tiền COD — Cứu 89 Đơn Thất Thoát Trong 0.25 Giây

## Bối cảnh Doanh nghiệp

**Công ty:** NevaB — Thương hiệu thời trang thiết kế nữ tại TP.HCM
**Quy mô:** 5.000 đơn hàng/tháng, bán Online qua Shopee/Lazada/Website
**Vấn đề:** Phụ thuộc 90% vào dịch vụ Giao Hàng Thu Tiền Hộ (Ship C.O.D)

## Nỗi đau hiện tại

Cuối mỗi tháng, Kế toán trưởng Mai nhận 2 file:

1. **File Nội bộ** (từ KiotViet): 5.200 đơn đã xuất kho
2. **File Đối tác** (từ GHTK): 4.950 đơn đã thu tiền

### Quy trình cũ (Thủ công)

- 3 kế toán viên ngồi `Ctrl+F` từng dòng suốt **4 ngày 4 đêm**
- Sai sót: ~15 đơn/tháng bị nhập nhầm dấu phẩy
- Kết luận cuối tháng: "Lỗ chênh lệch ~35 triệu chưa rõ nguyên nhân"

### Quy trình mới (Antigravity)

- 1 Prompt SUDO → AI viết Python → chạy xong trong **0.25 giây**
- Phát hiện chính xác **89 đơn bất thường** (47 thất thoát + 12 đơn ảo + 30 chênh lệch)

## Phân tích kỹ thuật

### Dữ liệu trong demo này

Thư mục `data/` chứa 2 file mẫu (thu nhỏ từ case study thực tế):

| File | Nội dung | Số dòng |
|---|---|---|
| `noi_bo.csv` | Đơn hàng từ KiotViet (VD001-VD020) | 20 |
| `doi_tac.csv` | Sao kê từ đối tác vận chuyển | 19 |

### Các lỗi được cài cắm (để AI phát hiện)

| # | Loại lỗi | Chi tiết | Nghiêm trọng |
|---|---|---|---|
| 1 | **Đơn thất thoát** | VD007 (Dang Van Giang, 320k) có ở nội bộ nhưng KHÔNG có ở đối tác | 🔴 Cao |
| 2 | **Đơn thất thoát** | VD011 (Ly Van Lam, 1.35 triệu — Hoàn trả) có ở nội bộ nhưng KHÔNG có ở đối tác | 🟡 Trung bình |
| 3 | **Đơn ảo** | VD099 (Khach Ao, 500k) chỉ có ở đối tác, KHÔNG có ở nội bộ | 🔴 Cao |
| 4 | **Chênh lệch tiền** | VD002: Nội bộ 1.250.000 vs Đối tác 1.200.000 (lệch 50k) | 🟡 Trung bình |
| 5 | **Chênh lệch tiền** | VD016: Nội bộ 3.400.000 vs Đối tác 3.350.000 (lệch 50k) | 🟡 Trung bình |
| 6 | **SĐT không chuẩn** | VD003: Nội bộ ghi `+84 933456789`, Đối tác ghi `0933456789` | ⚙️ Kỹ thuật |
| 7 | **SĐT có khoảng trắng** | VD005: Đối tác ghi `0955678901` (thừa dấu cách đầu) | ⚙️ Kỹ thuật |

### Kết quả kỳ vọng sau khi chạy

AI sẽ xuất file `ket_qua_doi_soat.xlsx` gồm:

- **Sheet 1 — THAT_THOAT:** 2 đơn (VD007, VD011)
- **Sheet 2 — DON_AO:** 1 đơn (VD099)
- **Sheet 3 — CHENH_LECH:** 2 đơn (VD002, VD016) — Ô tiền lệch được tô đỏ

## Bài học rút ra

1. **Prompt phải chỉ rõ cột chìa khóa** (Mã vận đơn) — Nếu không, AI sẽ đoán sai.
2. **Bước Clean data là QUAN TRỌNG NHẤT** — Không clean SĐT thì merge sẽ sai.
3. **Hàng rào an toàn** (Read-only, cấm đoán mò) giúp AI không tự bịa số liệu.
4. **ROI thực tế:** 3 người × 4 ngày = 12 ngày công → 0.25 giây. Tiết kiệm ~18 triệu VNĐ/tháng.

## Skill hỗ trợ

Xem [Skill Đối Soát Ngân Hàng](skills/doi_soat_ngan_hang/SKILL.md) để tái sử dụng cho dữ liệu thật.
