---
description: Theo dõi giá liên tục trong phiên giao dịch và bắn Alert Zalo/Telegram
---

# Nuôi Python Hẹn Giờ Báo Giá (Price Alert Daemon)

```bash
Nhập Lệnh Này Vào Khung Chat:
```

> Kích hoạt `/canh-bao-gia`
>
> 1. Gọi Skill `canh_bao_bien_dong_gia`.
> 2. Đọc file "Watchlist.xlsx" chứa danh sách mã và Điểm vào/Điểm cắt lỗ của tôi.
> 3. Khởi tạo Vòng lặp Loop (15 phút/lần). Dùng API để Check giá Market.
> 4. Gửi `Post Message` vào Telegram nếu: (A) Mã đó vượt mốc Break-out hoặc (B) Mã đó rớt qua mốc Cắt Lỗ. Cảnh bảo KHẨN CẤP.
