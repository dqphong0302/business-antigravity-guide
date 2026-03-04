---
name: Lọc CV Ứng Viên (ATS - Applicant Tracking)
description: Quét thư mục chứa CV (PDF/DOCX), trích xuất thông tin, chấm điểm theo tiêu chí JD, phân loại ứng viên Đạt/Không Đạt và di chuyển file tự động.
---

# Skill: Hệ Thống Lọc CV Tự Động (ATS Nội Bộ)

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi HR yêu cầu sàng lọc, đánh giá, hoặc phân loại hồ sơ ứng viên hàng loạt. Phù hợp cho đợt tuyển dụng lớn (>50 CV).

## Nguyên Liệu Đầu Vào

- **Thư mục CV:** Đường dẫn chứa các file PDF/DOCX của ứng viên.
- **File JD:** File `.txt` hoặc `.md` mô tả Yêu cầu Công việc (Job Description) với các tiêu chí bắt buộc.

## Quy Trình Thực Hiện

### Bước 1: Trích Xuất Nội Dung CV

- Duyệt tất cả file trong thư mục CV.
- Với file PDF: dùng `pdfplumber` hoặc `PyMuPDF` để extract text.
- Với file DOCX: dùng `python-docx` để extract text.
- Lưu nội dung text của mỗi CV vào một Dictionary {tên_file: nội_dung}.

### Bước 2: Phân Tích & Chấm Điểm

- Đọc file JD, xác định các Tiêu chí Rubric:
  - Kinh nghiệm tối thiểu (năm) → Tìm pattern "X năm kinh nghiệm" trong CV.
  - Kỹ năng bắt buộc → Tìm keywords trong CV (ví dụ: "Python", "Excel", "IELTS").
  - Bằng cấp → Tìm pattern "Đại học", "Thạc sĩ", tên trường.
- Gán điểm cho mỗi tiêu chí (thang 0-10). Tính tổng điểm.

### Bước 3: Phân Loại & Di Chuyển File

- Nếu Tổng Điểm >= Ngưỡng Đạt (mặc định 6/10):
  - Di chuyển file CV gốc vào thư mục `/Moi_Phong_Van/`.
- Nếu Tổng Điểm < Ngưỡng:
  - Di chuyển file CV gốc vào thư mục `/Tu_Choi/`.

### Bước 4: Xuất Bảng Xếp Hạng

- Tạo file `Ket_Qua_Loc_CV.xlsx` với các cột: Tên File, Tên Ứng Viên, Tổng Điểm, Chi Tiết Điểm, Trạng Thái (Đạt/Không Đạt).
- Sắp xếp theo Tổng Điểm giảm dần.
- Tô xanh các dòng Đạt, tô đỏ các dòng Không Đạt.

## Lưu Ý Quan Trọng

- Giữ bản gốc CV trong thư mục backup trước khi di chuyển.
- Nếu file CV bị lỗi đọc (encrypted PDF), ghi vào danh sách "CV_Loi" và bỏ qua.
- KHÔNG tự ý loại ứng viên dựa trên giới tính, tuổi tác, hoặc quê quán (Tuân thủ Luật Lao động).
