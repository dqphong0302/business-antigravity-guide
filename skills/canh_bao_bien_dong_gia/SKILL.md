---
name: Cảnh Báo Biến Động Giá (Price Volatility Alert)
description: Khởi chạy luồng giám sát thị trường (Cronjob/Loop), theo dõi giá cổ phiếu theo thời gian thực và tự động gửi tin nhắn (Telegram/Zalo) khi chạm ngưỡng cắt lỗ/chốt lời.
---

# Skill: Lính Gác Cảnh Báo Giá Thị Trường (Volatility Alert)

## Bối Cảnh Sử Dụng

Lãnh đạo bận họp, không thể dán mắt vào bảng điện tử xanh đỏ cả ngày. Việc quên cắt lỗ khi giá rớt thủng hỗ trợ dẫn đến việc "kẹp hàng" sâu. Skill này biến AI thành người theo dõi bảng điện hộ sếp.

## Nguyên Liệu Đầu Vào

- Danh sách mã cổ phiếu cần theo dõi (Watchlist): Vd: FPT, MWG, VCB.
- Ngưỡng Giá Báo Động (Thresholds): Gồm giá cắt lỗ (Stop-loss), giá chốt lời (Take-profit), hoặc Volume đột biến.
- Webhook URL hoặc API Token của Telegram/Zalo.

## Quy Trình Thực Hiện

### Bước 1: Thu Thập Giá Real-time

- Thiết lập một tiến trình Python chạy vòng lặp (Cứ mỗi 5-15 phút lấy giá một lần) trong giờ hành chính giao dịch (9:00 - 14:45).
- Lấy thông tin từ các cổng Open API chứng khoán (Giá hiện tại, Khối lượng giao dịch).

### Bước 2: Đánh Giá So Khớp Điều Kiện

```python
# Pseudo-code cảnh báo
for co_phieu in watchlist:
    if gia_hien_tai[co_phieu] <= vung_cat_lo[co_phieu]:
        Bao_Dong_Khong_Gian_Do()
        Gui_Tin_Nhan_Telegram(f"CẢNH BÁO: {co_phieu} thủng mốc cắt lỗ. Giá hiện tại {gia_hien_tai}. ĐỀ NGHỊ BÁN NGAY BẢO TOÀN VỐN.")
    elif khoi_luong_hien_tai[co_phieu] > khoi_luong_trung_binh_20_ngay * 3:
        Gui_Tin_Nhan_Telegram(f"CHÚ Ý: {co_phieu} NỔ VOLUME KHỦNG (Gấp 3 lần TB). Dòng tiền lớn tham gia, xem xét chốt lời hoặc giữ chặt.")
```

### Bước 3: Kích Hoạt Hệ Thống Báo Động

- Không đợi Sếp mở app Antigravity ra mới thông báo. AI sẽ chủ động "Push" (Đẩy) thông báo thẳng vào điện thoại của Sếp thông qua Zalo Message API hoặc Telegram Bot.

## Ví Dụ Prompt Gọi Skill

```
"Hãy chạy một Daemon ẩn theo dõi 3 mã: SSI, VND, HCM. 
Lấy giá từ Web Chứng Khoán. Nếu SSI rớt xuống dưới 30.0, hoặc VND tăng vượt 22.5. 
Lập tức gửi 1 tin nhắn vào Telegram Bot của tôi báo tin. 
Kiểm tra ngầm mỗi 15 phút đến khi hết phiên chiều. Đừng làm phiền tôi nếu không chạm ngưỡng này."
```
