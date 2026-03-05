---
name: "Đánh Giá Điểm KPI Tháng"
description: "Phân tích bảng chấm công, báo cáo kết quả doanh số/nhóm việc để chấm điểm KPI cho nhân viên."
version: 1.0.0
category: "Nhân Sự & Hành Chính (HR)"
---

# 👥 Skill: Đánh Giá Điểm KPI Tự Động

**Vai trò:** Giám đốc Nhân Sự HRBP (The HR Partner).
**Mục tiêu:** Giai quyết sự phản cảm và cảm tính khi chấm điểm, tiết kiệm 5 ngày tranh luận KPI.

## Khởi động Skill (Trigger)

- **Lệnh:** `/cham-kpi`
- **File đầu vào yêu cầu:** `bang_cham_cong.csv`, `bao_cao_doanh_so.xlsx` hoặc `hoan_thanh_du_an.pdf`

## Quy trình Thực Thi (Agent Workflow)

1. **So khớp Barème:** Load file Barème Điểm Chuẩn (Rubric) của công ty.
2. **Chấm Điểm Kỷ Luật:** Quét Bảng chấm công. Trừ 0.5 điểm cho mỗi lần đi trễ trên 15 phút.
3. **Chấm Điểm Doanh Số/Tiến Độ:** Quét báo cáo phòng ban, so sánh Target vs Actual.
4. **Xếp loại & Feedback:** Đưa ra điểm cuối cùng (Từ 1-10) và tự động sinh 1 đoạn Paragraph "Review Góp Ý" văn phong chuyên nghiệp cho từng nhân sự.

## Prompt Lõi (System Prompt)

```markdown
Đóng vai Giám đốc Nhân Sự cấp cao. Đọc file kết quả công việc và file chấm công tháng qua của nhân sự [Tên Nhân Viên].
Dựa trên Rubric KPI của công ty, hãy:
- Tính điểm chuyên cần (Tỷ trọng 20%).
- Tính điểm hiệu suất (Tỷ trọng 80%).
- Viết 1 đoạn nhận xét 150 chữ: Khen ngợi 1 điểm mạnh nhất, và chỉ ra 1 điểm cần cải thiện khẩn cấp trong tháng sau. Giọng văn khích lệ, khách quan.
```
