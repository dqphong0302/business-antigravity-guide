---
description: Cảnh báo tồn kho chạm ngưỡng và tự động đặt hàng bổ sung (Kho / Mua hàng)
---

# Cảnh Báo Tồn Kho & Tự Động Đặt Hàng

// turbo-all

Quy trình giám sát kho tự động:

1. Đọc file tồn kho hiện tại tại `/Kho/Ton_Kho_HienTai.xlsx`.
2. Quét cột `So_Luong_Ton`. So sánh với cột `Muc_Toi_Thieu` (Min Level).
3. Nếu `So_Luong_Ton` <= `Muc_Toi_Thieu`:
   - Ghi danh sách sản phẩm cần bổ sung vào `Canh_Bao_Het_Hang.xlsx`.
   - Tính số lượng cần đặt: `Muc_Toi_Uu - So_Luong_Ton`.
4. Soạn email đặt hàng mẫu cho từng nhà cung cấp (tên NCC lấy từ cột `Nha_Cung_Cap`).
5. In cảnh báo lên Terminal: "🚨 [X] sản phẩm sắp hết hàng. File chi tiết: Canh_Bao_Het_Hang.xlsx"
