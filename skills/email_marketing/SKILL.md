---
name: Gửi Email Marketing Hàng Loạt (Bulk Email Campaign)
description: Đọc danh sách khách hàng, cá nhân hóa nội dung email theo tên/sản phẩm quan tâm, và gửi hàng loạt qua SMTP hoặc API.
---

# Skill: Chiến Dịch Email Marketing Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Marketing cần gửi email quảng bá, thông báo khuyến mãi, hoặc chăm sóc khách hàng cũ với nội dung cá nhân hóa.

## Quy Trình Thực Hiện

1. Đọc file Khách hàng (`ds_khach_hang.xlsx`): Tên, Email, SP đã mua, Ngày mua gần nhất.
2. Đọc file Template Email (`template_email.html` hoặc `.txt`).
3. Thay thế biến placeholder: `{{TEN_KHACH}}`, `{{SAN_PHAM}}`, `{{NGAY_MUA}}`.
4. Dùng thư viện `smtplib` Python kết nối SMTP server.
5. Gửi từng email với delay 2-5 giây giữa các email (tránh bị đánh spam).
6. Ghi log: Email nào gửi thành công, email nào bị bounce/lỗi.

## Lưu Ý

- PHẢI có nút Unsubscribe trong email (Tuân thủ Luật chống Spam).
- Người dùng phải cung cấp SMTP credentials (không lưu mật khẩu trong file skill).
- Giới hạn tối đa 500 email/ngày (tùy nhà cung cấp SMTP).
