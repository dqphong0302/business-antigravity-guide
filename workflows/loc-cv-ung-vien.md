---
description: Lọc và chấm điểm CV ứng viên hàng loạt theo JD (Phòng HR)
---

# Sàng Lọc CV Ứng Viên

// turbo-all

Quy trình tuyển dụng tự động:

1. Đọc Skill `loc_cv_ung_vien` tại `/skills/loc_cv_ung_vien/SKILL.md`. Tuân thủ quy trình.
2. Thư mục CV: `/HR/TuyenDung/CV_DotX/` — chứa file PDF/DOCX.
3. File JD: `/HR/TuyenDung/JD_ViTri.txt` — chứa yêu cầu công việc.
4. Trích xuất text từ từng CV (dùng pdfplumber cho PDF, python-docx cho DOCX).
5. Chấm điểm theo Rubric trong JD (thang 10). Phân loại:
   - Điểm >= 6: Di chuyển CV vào `/HR/TuyenDung/Moi_Phong_Van/`.
   - Điểm < 6: Di chuyển vào `/HR/TuyenDung/Tu_Choi/`.
6. Xuất file `Ket_Qua_Loc_CV.xlsx` xếp hạng giảm dần. Tô xanh dòng Đạt, đỏ dòng Không Đạt.
7. In tóm tắt: Tổng CV, Số Đạt, Số Không Đạt, Top 5 ứng viên.
