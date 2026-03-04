---
description: Đối soát COD cuối tháng giữa KiotViet và đối tác vận chuyển (Kế toán)
---

# Đối Soát COD Cuối Tháng

// turbo-all

Hỡi Đặc Vụ Antigravity, kích hoạt quy trình Đối soát COD:

1. Đọc Skill `doi_soat_ngan_hang` tại thư mục `/skills/doi_soat_ngan_hang/SKILL.md`. Làm theo đúng quy trình 3 Agent trong đó.
2. File nội bộ: Tìm file Excel/CSV mới nhất trong thư mục `/KeToan/DuLieu_Thang/` có chứa từ "noi_bo" hoặc "kiotviet" trong tên.
3. File đối tác: Tìm file có chứa từ "doi_tac" hoặc "ghtk" hoặc "viettel_post" trong cùng thư mục.
4. Cột chìa khóa merge: "ma_don" hoặc "ma_van_don" (trim + uppercase trước).
5. Xuất kết quả `Doi_Soat_COD_ThangX.xlsx` gồm 3 sheets (Thất thoát, Đơn ảo, Chênh lệch tiền). Tô đỏ ô lệch.
6. In tóm tắt: Số đơn mỗi nhóm + Tổng tiền ảnh hưởng.
