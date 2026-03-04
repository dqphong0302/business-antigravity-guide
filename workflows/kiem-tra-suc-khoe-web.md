---
description: Theo dõi sức khỏe hệ thống website (IT / DevOps)
---

# Automap - Cấp Cứu Website

// turbo-all

Quy trình tuần tra sức khỏe Hệ thống Web:

1. Bạn hãy tự động ping hoặc dùng `curl` kiểm tra mã trạng thái (HTTP Status Code) các domain chính của công ty chúng ta.
2. Yêu cầu mã trả về phải là 200 OK. Đo lường thời gian phản hồi (Response Time).
3. Nếu phát hiện ra Lỗi 404 (Not Found) hay Lỗi 500 (Internal Server Error):
    - Khởi động quy trình Debug bằng cách soi Log (nếu được trỏ đường dẫn truyệt đối vào file log).
    - Phát đi Cảnh Báo Ephemeral Message khẩn cấp lên màn hình cho Quản trị viên.
4. In Báo cáo sức khỏe tổng quát vào màn hình Chat.
