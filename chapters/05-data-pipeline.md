# Chương Chuyên Sâu: Kỹ Sư Dữ Liệu Tự Động - Đọc, Xử Lý, Đối Chiếu File Và Lập Báo Cáo Đo Lường

## 1. Mở Đầu: Tội Ác Của Việc "Dò File Bằng Mắt"

Ở các doanh nghiệp Vận tải, Ecommerce, hay Kế toán dịch vụ, quy trình khủng khiếp nhất cuối mỗi tháng là: **Đối soát chéo (Reconciliation)**.

- Bạn có 1 file Bảng kê bán hàng từ phần mềm KiotViet của Công ty (10,000 dòng).
- Bạn có 1 file Bảng đối soát thu hộ C.O.D từ đơn vị Giao Hàng Tiết Kiệm gửi sang (9,800 dòng).
Việc của bạn là tìm ra 200 dòng bị rớt, bị sai lệch số tiền, hoặc chưa thanh toán giữa 2 file này. Nếu làm bằng tay hoặc dùng hàm Excel VLOOKUP mà số điện thoại bên kia thừa 1 khoảng trắng, Excel sẽ báo `#N/A`. Nhân viên ngồi dò bằng mắt suốt 3 đêm liền, hoa mắt nhức đầu và cuối cùng vẫn sai số 5 triệu đồng.

Trong chuyên đề Đặc biệt này, chúng ta sẽ ứng dụng **Kiến trúc Chia Task đa Tác nhân (Multi-Agent Task Division)** của Antigravity để xử lý bài toán Đọc file -> Đối chiếu chéo -> Lập Báo cáo Bất thường. Bạn sẽ học cách làm Giám đốc giao việc, vỡ bài toán ra thành các Sudo Code (Mã giả) để AI tự động code Python xử lý.

---

## 2. Ý Tưởng Tự Động Hóa Đối Chiếu: Tuyệt Chiêu "Ba Người Thợ"

Đừng quăng 2 file Excel bắt AI làm một lèo từ A-Z. Hãy chia nó thành một Dây chuyền sản xuất có 3 thợ (Sub-Agents):

1. **Thợ Dọn Dẹp (Data Cleaner Agent):** Chỉ tập trung vào việc Đọc file `File_Cty.xlsx` và `File_DoiTac.csv`. Cắt bỏ khoảng trắng dư thừa, đưa tất cả Mã Đơn Hàng về in hoa, bỏ số 0 ở đầu SĐT để 2 bảng đồng bộ định dạng (Format).
2. **Thợ So Sánh (Data Comparator Agent):** Gộp 2 bảng lại làm 1. Tìm các dòng có ở Bảng A mà không có ở Bảng B. Tìm các dòng có Mã giống nhau nhưng Cột Số Tiền bị lệch.
3. **Thợ Lập Báo Cáo (Reporter Agent):** Nhận kết quả lỗi từ Thợ 2. Tô màu đỏ các dòng sai lệch, xuất ra một file Excel tên `Bao_Cao_Chenh_Lech.xlsx` để Sếp Kế toán gọi điện mắng đối tác.

---

## 3. Cách Thực Hành: Điều Phái AI Bằng Sudo Prompt & Sudo Code

Dưới đây là cách bạn (User) ứng dụng Antigravity vào công việc đối soát chéo phức tạp này. Bạn sẽ copy y nguyên câu Prompt dưới đây ném vào thanh Chat.

### Sudo Prompt (Ra Lệnh Khởi Lập Dây Chuyền Đối Chiếu File)

> **SUDO PROMPT: (Copy paste để giao việc cho Antigravity)**
>
> "Chúng ta sẽ lập một dây chuyền Data Analyst tự động tại thư mục `/Doi_Soat_T4`.
> Tôi có 2 file chứa Data thô là `Data_A_KiotViet.xlsx` và `Data_B_GHTK.csv`. Cột mấu chốt để đối chiếu là 'Mã Vận Đơn'.
>
> **Hãy phân chia làm 3 Sub-Agent xử lý theo luồng Task sau:**
>
> **[Agent 1 - Chuẩn Hóa]**
> Sử dụng Python Pandas đọc 2 file. Xóa mọi khoảng trắng (Trim) và in hoa (Uppercase) cột 'Mã Vận Đơn'. Sửa cột 'Số Điện Thoại' về định dạng chuẩn (bắt đầu bằng +84). Tạo ra 2 bảng `Data_A_Clean` và `Data_B_Clean`.
>
> **[Agent 2 - Đối Chiếu Chéo]**
> Dùng hàm `merge` của Pandas với cơ chế Outer Join.
> Yêu cầu:
>
> 1. Trích xuất những Mã Vận Đơn chỉ xuất hiện ở File A. (Cảnh báo: Đơn đi mà chưa ghi nhận).
> 2. Trích xuất những Mã Vận Đơn chỉ xuất hiện ở File B. (Cảnh báo: Cố tình chèn đơn khống).
> 3. Trích xuất những Mã Vận Đơn có ở cả hai file, nhưng so sánh hiệu số (Cột Tiền File A - Cột Tiền File B) bị lệch lớn hơn 0 đồng.
>
> **[Agent 3 - Xuất Báo Cáo Cuối]**
> Dùng thư viện `openpyxl`. Gom 3 kết quả từ Agent 2 vào 3 sheet (trang tính) khác nhau trong cùng 1 file Excel tên là `BaoCao_ChechLech_Chinh_Thuc.xlsx`. Bôi nền màu đỏ gạch ở các ô Số tiền bị lệch để tôi dễ nhìn.
>
> Viết một file Python tổng hợp `main_doi_soat.py` chứa mô hình này và tự động chạy Bash `python main_doi_soat.py` ngay để tôi nghiệm thu kết quả!"

---

### Sudo Code Mẫu (Ruột Code Do Agent Tự Đẻ Ra)

Khi AI nhận được Prompt trên, nó hiểu ngay nó phải làm gì. Nó sẽ không than vãn, không xin nghỉ ốm, tự động vận dụng Pandas (Vua Dữ Liệu) tạo ra dòng chảy mã hóa y hệt khối Sudo Code sau đây trong vòng 10 giây:

```python
# SUDO CODE MẪU: Pipeline Xử lý & Đối chiếu Đa Bảng (Cho File main_doi_soat.py)
Import Thu_Vien("Pandas");
Import Thu_Vien("OpenPyXL_Report");

// ---------------------------------------------------------
// [Agent 1] Mảnh Ghép Dọn Dẹp (Data Cleaning)
// ---------------------------------------------------------
Ham Don_Dep_Rong_Ran(File_Duong_Dan, Cot_Ma_Chuan):
    Bang_Du_Lieu = Pandas.Doc_Tap_Tin(File_Duong_Dan);
    
    // Loại bỏ dấu cách đầu cuối, in hoa lên tránh lệch text (vd: mdh123 != MDH123)
    Bang_Du_Lieu[Cot_Ma_Chuan] = Bang_Du_Lieu[Cot_Ma_Chuan].Thay_Doi_Chu(In_Hoa).Xoa_Khoang_Trang();
    
    // Quét và nắn lại Cột số tiền (Chuyển chuỗi "25.000 VNĐ" thành số Integer 25000)
    Bang_Du_Lieu['SoTiens'] = Bang_Du_Lieu['So_Tien'].Cat_Chu_Thanh_So(); 
    Tra_Ve Bang_Du_Lieu;

// Thực thi Agent 1
Data_Noi_Bo = Don_Dep_Rong_Ran("Data_A_KiotViet.xlsx", Cot_Ma="Mã Vận Đơn");
Data_Doi_Tac = Don_Dep_Rong_Ran("Data_B_GHTK.csv", Cot_Ma="Ma_Van_Don");

// ---------------------------------------------------------
// [Agent 2] Mảnh Ghép So Sánh (Data Comparator)
// ---------------------------------------------------------
// Gán 2 bảng cạnh nhau, tìm điểm mù
Bang_Gop_Chung = Pandas.Ghep_Chung_2_Bang(Data_Noi_Bo, Data_Doi_Tac, Khoa_Chinh="Mã Vận Đơn", Kieu="Tat_Ca_Outer");

// Phân luồng Cảnh Báo
Canh_Bao_Mat_Don_Hang = Bang_Gop_Chung.Loc(Dieu_Kien = "Có ở Data Nội Bộ Tồn Tại, Có Ở Data Đối Tác = NULL");
Canh_Bao_Chua_Khong = Bang_Gop_Chung.Loc(Dieu_Kien = "Có ở Nội Bộ = NULL, Có ở Đối Tác Tồn Tại");

// Tìm Kẻ Gian lận lệch tiền
Dieu_Kien_Lech = (Bang_Gop_Chung['SoTien_NoiBo'] - Bang_Gop_Chung['SoTien_DoiTac']) != 0;
Cac_Don_Lech_Tien = Bang_Gop_Chung.Loc(Dieu_Kien_Lech);

// ---------------------------------------------------------
// [Agent 3] Mảnh Ghép Excel Báo Cáo (Reporter Excel)
// ---------------------------------------------------------
// Ghi 3 Tab (Sheets) vào 1 file Excel cho Sếp Kế toán
Ghi_Tep_Excel = Pandas.Mo_But_Ghi("BaoCao_ChechLech_Chinh_Thuc.xlsx");
Canh_Bao_Mat_Don_Hang.Xuat_Ra_Sheet(Ghi_Tep_Excel, Ten_Sheet="Mất Ghi Nhận");
Canh_Bao_Chua_Khong.Xuat_Ra_Sheet(Ghi_Tep_Excel, Ten_Sheet="Chêm Hàng Khống");
Cac_Don_Lech_Tien.Xuat_Ra_Sheet(Ghi_Tep_Excel, Ten_Sheet="Bị Lệch Số Tiền");

// Highlight bôi đỏ ô lệch
OpenPyXL_Report.Mo_File_Đã_Luo();
OpenPyXL_Report.Chon_Sheet("Bị Lệch Số Tiền").Quét_Từ_Trên_Xuống().Neu(Lech != 0).To_Mau_Nen(Do_Ruc_Rỡ);
OpenPyXL_Report.Dong_Va_Luu();

In_Ra_Man_Hinh("Hoàn thành quá trình đối soát 20.000 dòng. Không sai sót 1 VNĐ. Tổng thời gian xử lý: 0.15 Giây.");
```

## 4. Tổng Kết Giá Trị Chuyển Đổi Số Cuối Cùng

Qua quy trình Đọc - Đối Chiếu - Lập báo cáo này, bạn có thể tự thay tên File áp dụng được cho **mọi ngóc ngách của công việc:**

1. **Phòng Nhân Sự HR:** Đối soát Số ngày quét vân tay chấm công (File Máy tính) và Đơn xin nghỉ phép qua tin nhắn Zalo/Giấy (Báo cáo lệch).
2. **Kế Toán Kho bãi:** Đối chiếu File Xuất kho thủ kho với File Quét Barcode dán trên kiện hàng (Chống ăn cắp).
3. **Phòng Mua Hàng:** Đưa 1 bản Báo cáo Mẫu cũ (2024) và 1 bản Báo giá mới (2025). Gọi AI đối chiếu để xem từng mặt hàng tăng giảm giá ra sao, phát hiện mặt hàng gài giá tăng bất hợp lý.

Ứng dụng Antigravity không phải là một Cuộc thi gõ code hay. Ứng dụng AI là Nghệ thuật của sự Lười Biếng Thông Minh: **"Làm sao để tôi nói đúng 1 câu Phân chia Task, 3 Agent ảo tự bóc tách ra làm, và 1 file chốt lỗi bôi đỏ đập thẳng vào mắt tôi?"**

---

## 5. Case Study Thực Tế

### 📋 Case Study: Công Ty Ecommerce "ShopViet" — Đối Soát COD Với Giao Hàng Tiết Kiệm

**Bối cảnh:** ShopViet bán hàng trên Shopee & Lazada, ship COD qua GHTK. Mỗi tuần có ~3,000 đơn hàng. Cuối tháng, Kế toán nhận 2 file:

- **File A:** Bảng kê bán hàng từ KiotViet (3,200 dòng — vì có đơn hủy/hoàn).
- **File B:** Bảng đối soát thu hộ từ GHTK (2,950 dòng).

Kế toán phải tìm ra: (1) Đơn nào ship rồi mà GHTK chưa trả tiền? (2) Đơn nào GHTK báo đã chuyển nhưng KiotViet không có — có thể là đơn khống? (3) Đơn nào số tiền bị lệch giữa 2 bên?

Trước đây: 2 kế toán ngồi VLOOKUP mất **3 ngày**, sai sót ~5 triệu đồng/tháng.

**Giải pháp — Gọi Skill [`doi_soat_ngan_hang`](../skills/doi_soat_ngan_hang/SKILL.md):**

> *"Antigravity, dùng Skill đối soát ngân hàng. File A: `/DoiSoat/KiotViet_T8.xlsx`, cột khóa: 'Mã Vận Đơn'. File B: `/DoiSoat/GHTK_T8.csv`, cột khóa: 'Ma_Van_Don'. Chuẩn hóa: trim + uppercase cột khóa, bỏ dấu phẩy cột tiền. Tìm: (1) Có ở A mà không có ở B, (2) Có ở B mà không có ở A, (3) Có ở cả hai nhưng tiền lệch. Xuất `BaoCao_DoiSoat_T8.xlsx` với 3 sheet, tô đỏ ô lệch."*

**Kết quả:**

- ⏱️ Thời gian: **8 giây** (thay vì 3 ngày).
- 🔍 Phát hiện: 47 đơn GHTK chưa trả tiền (tổng 12.8 triệu), 3 đơn nghi khống, 15 đơn lệch số tiền do phí ship.
- 💰 CEO gọi điện cho GHTK ngay chiều hôm đó → Thu hồi 12.8 triệu trong 24h.

---

## 6. Bảng Tổng Hợp Skills Áp Dụng Cho Chương Này

| Vấn đề cần giải quyết | Skill tương ứng | Khi nào dùng |
| :--- | :--- | :--- |
| Đối chiếu 2 file Excel/CSV | [`doi_soat_ngan_hang`](../skills/doi_soat_ngan_hang/) | Cuối tháng đối soát COD, sao kê NH, bảng kê thuế |
| Tổng hợp nhiều file doanh thu | [`bao_cao_doanh_thu`](../skills/bao_cao_doanh_thu/) | Gộp data từ nhiều chi nhánh/ngày |
| Cảnh báo tồn kho sắp hết | [`canh_bao_ton_kho`](../skills/canh_bao_ton_kho/) | Quét tồn kho hàng ngày, gửi alert Telegram |
| Hỗ trợ quyết định tăng/giảm giá | [`phan_tich_quyet_dinh`](../skills/phan_tich_quyet_dinh/) | Phân tích elasticity trước khi điều chỉnh giá |

---

*(Chương tiếp: AI trong Ra Quyết Định Kinh Doanh — Từ "Linh Cảm" sang "Data-Driven".)*
