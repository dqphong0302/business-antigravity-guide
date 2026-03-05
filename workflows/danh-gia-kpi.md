---
description: "Tự động chấm KPI và viết Feedback cho nhân sự cuối tháng"
---

# Lệnh: `/cham-kpi`

**Phòng ban:** Nhân Sự & Hành Chính (HR)

## Kịch Bản Luồng Chạy (Workflow Execution)

1. Thu thập file Chấm công `.csv` từ máy chấm công vân tay.
// turbo
2. Xin quyền đọc báo cáo thành tích/doanh số từ thư mục của nhân sự.
// turbo
3. Chạy kỹ năng `danh_gia_kpi` để đối chiếu với Rubric Điểm Chuẩn của công ty.
// turbo
4. Export ra bảng Excel chứa Điểm Số, Xếp loại (A, B, C) và cột Feedback (khen/chê).
// turbo
5. Tự động soạn sẵn 50 đoạn tin nhắn cho 50 nhân sự nhưng lưu dưới dạng Draft chờ Giám đốc Nhân sự (HRD) bấm gửi.
