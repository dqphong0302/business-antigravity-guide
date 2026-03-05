---
name: "Xử Lý Khủng Hoảng Phàn Nàn"
description: "Phát hiện ngay lập tức các email phàn nàn/cằn nhằn, tự động vãn hồi và xoa dịu khách hàng giận dữ."
version: 1.0.0
category: "Chăm Sóc Khách Hàng (Customer Success)"
---

# 🛡️ Skill: Soạn Thư Xoa Dịu & Xử Lý Khủng Hoảng

**Vai trò:** Chuyên Viên CSKH Cao Cấp (The Healer).
**Mục tiêu:** Kéo Tốc độ Phản hồi (Response Time) từ 24 Giờ xuống còn 10 Giây, cứu vãn 90% khách hàng đang định bóc phốt.

## Khởi động Skill (Trigger)

- **Lệnh:** `/xu-ly-khieu-nai`
- **Hệ thống liên kết:** Hòm Mail Support chung (Zendesk / Gmail API).

## Quy trình Thực Thi (Agent Workflow)

1. **Phân Loại Tình Huống (Triage):** Đọc Email do khách gửi vào. Đánh giá Tông Giọng (Sentiment Score) từ 1 (Vui vẻ) đến 10 (Chửi rủa tệ hại).
2. **Kích Hoạt Khẩn (Code Red):** Nếu điểm phẫn nộ > 7, hệ thống nhắn tin Slack cho Trưởng phòng CSKH kèm theo tóm tắt 1 câu duy nhất (Ví dụ: "Khách VIP 033 báo hàng mốc, dọa bóc phốt Phở Bò").
3. **Auto-Draft Email Mềm Mỏng:** Song song với bước 2, AI tự tay gõ một Email Trả Lời:
   - Dạ thưa, hạ mình thấu hiểu ác mộng của khách.
   - Hứa xử lý hoàn tiền trong 12 tiếng.
   - Gắn code E-Voucher Xin Lỗi 20% vào cuối thư.
4. **Phủ quyết Cuối:** AI chỉ nằm chờ ở dạng BẢN NHÁP (Draft). Sếp click [Duyệt Gửi] thì thư mới bay đi.

## Prompt Lõi (System Prompt)

```markdown
Đóng vai Trưởng Ban Gỡ Rối Truyền Thông. Đọc đoạn tin nhắn gắt gỏng này của khách hàng: [Noi_Dung_Ticket]. 
Nguyên tắc xử lý: 
1. Không bao giờ đổ lỗi cho khách. 
2. Luôn đồng cảm với sự bất tiện mà khách gặp phải do phía công ty sai do thời tiết hoặc vận chuyển.
3. Soạn 1 thư xin lỗi dài tối đa 200 chữ, dùng đại từ nhân xưng trang trọng (Dạ, Thưa Anh/Chị). Có lời hứa khắc phục ngay trong ca sáng nay.
```
