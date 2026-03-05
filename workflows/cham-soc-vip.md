---
description: "Quét CRM và tự động soạn tin nhắn chăm sóc Khách VIP"
---

# Lệnh: `/cham-soc-vip`

**Phòng ban:** Sales B2B & Customer Success

## Kịch Bản Luồng Chạy (Workflow Execution)

1. Chạy ngầm vào 08:00 AM mỗi sáng. Kết nối trực tiếp vào API của CRM (Hubspot/Bitrix24).
// turbo
2. Lọc ra danh sách khách VIP thỏa các điều kiện: Sắp tới Sinh nhật, Vừa lên hạng, hoặc >60 ngày chưa chốt giao dịch mới.
// turbo
3. Nạp Data vào kỹ năng `cham_soc_vip`.
// turbo
4. Gen kịch bản Zalo nhắn cá nhân hóa tuyệt đối (gọi đúng tên thật, nhắc đúng sở thích từ Note trên CRM).
// turbo
5. In ra Console Terminal danh sách 5 tin nhắn nháp ngày hôm nay để Sales Director duyệt.
