# Phụ Lục: Kho Prompt Multi-Agent Mẫu — Copy-Paste & Chạy Ngay Trên Antigravity

> 💡 Mỗi Prompt dưới đây đã được kiểm thử trên [Antigravity](https://antigravity.google). Bạn chỉ cần **thay tên file/thư mục** cho phù hợp với dữ liệu công ty rồi paste vào Chat Panel.

---

## 1. 📊 Đối Soát Doanh Thu Đa Kênh (Kế Toán / CFO)

**Bài toán:** So khớp doanh thu từ 3 nguồn (POS, Shopee, Ngân hàng) để tìm chênh lệch.

```
SUDO PROMPT: ĐỐI SOÁT DOANH THU ĐA KÊNH THÁNG 11

👑 [VAI TRÒ]
Bạn là Kiểm Toán Viên Nội Bộ Cấp Cao. Mục tiêu: Tìm mọi giao dịch chênh lệch giữa 3 nguồn dữ liệu.

⚙️ [MẠNG LƯỚI ĐA ĐẶC VỤ]

📥 [Agent 1 — Thợ Dọn Dẹp Dữ Liệu (Data Cleaner)]
Đọc 3 file:
- /Data/DoanhThu_POS_T11.xlsx
- /Data/DoanhThu_Shopee_T11.csv
- /Data/SaoKe_NganHang_T11.xlsx
Chuẩn hóa: Xóa khoảng trắng thừa, định dạng cột Ngày về dd/mm/yyyy, cột Tiền về số nguyên. Lưu 3 file sạch vào /tmp/.

⚖️ [Agent 2 — Trọng Tài So Khớp (Reconciler)]
Nhận 3 file sạch từ Agent 1. Merge theo Mã Đơn Hàng (outer join).
Phân loại:
- ✅ KHỚP: Có ở cả 3 nguồn, số tiền giống nhau (sai lệch < 1,000đ).
- 🔴 MẤT: Có ở POS nhưng không có ở Ngân hàng (tiền chưa về).
- ⚠️ LỆCH: Có ở cả 3 nhưng số tiền khác nhau.

📄 [Agent 3 — Báo Cáo Tổng Hợp (Report Builder)]
Xuất file Excel DoiSoat_T11.xlsx gồm:
- Sheet "Tổng Quan": Tổng doanh thu mỗi kênh, số giao dịch khớp/mất/lệch.
- Sheet "Chi Tiết Lệch": Danh sách giao dịch lệch, tô đỏ dòng chênh > 500,000đ.
- Sheet "Mất Tiền": Danh sách giao dịch có ở POS nhưng chưa nhận tiền.

🚧 [RÀNG BUỘC] Cấm sửa file gốc. Ghi "N/A" nếu thiếu cột. Thông báo tổng số tiền chênh lệch khi hoàn tất.
```

---

## 2. 🕸️ Cào Giá Đối Thủ Đa Sàn (Marketing / Kinh Doanh)

**Bài toán:** Thu thập giá 30 sản phẩm trên Shopee + Tiki + Lazada, so với giá nội bộ.

```
SUDO PROMPT: TRINH SÁT GIÁ ĐỐI THỦ ĐA SÀN THƯƠNG MẠI ĐIỆN TỬ

👑 [VAI TRÒ]
Bạn là Trưởng Ban Tình Báo Giá (Pricing Intelligence Lead). Mục tiêu: Cào giá 30 sản phẩm mỹ phẩm trên 3 sàn TMĐT, so với bảng giá nội bộ.
File nội bộ: /Data/BangGia_NoiBo.xlsx (cột: Tên SP, Mã SP, Giá bán lẻ)

⚙️ [MẠNG LƯỚI ĐA ĐẶC VỤ — MÔ HÌNH FAN-OUT]

🕸️ [Agent A — Trinh Sát Shopee]
Mở trình duyệt. Tìm lần lượt 30 tên sản phẩm trên shopee.vn.
Thu thập: Tên SP, Giá bán, % Giảm giá, Số lượt bán. Lưu vào /tmp/gia_shopee.csv.

🕸️ [Agent B — Trinh Sát Tiki]
Mở trình duyệt. Tìm trên tiki.vn. Thu thập tương tự Agent A. Lưu /tmp/gia_tiki.csv.

🕸️ [Agent C — Trinh Sát Lazada]
Mở trình duyệt. Tìm trên lazada.vn. Thu thập tương tự. Lưu /tmp/gia_lazada.csv.

📊 [Agent D — Phân Tích Gia Tổng Hợp (Price Analyst)]
Đọc 3 file từ Agent A/B/C + file nội bộ. Merge theo Tên SP.
Tính: Giá thấp nhất thị trường, Chênh lệch vs giá nội bộ (%).
Đánh dấu: 🔴 SP đắt hơn đối thủ > 15%, 🟢 SP rẻ hơn, 🟡 Ngang bằng.
Xuất file SoSanh_Gia_DaKenh.xlsx + biểu đồ cột lưu SoSanh_Gia.png.

🚧 [RÀNG BUỘC] Nếu không tìm thấy SP, ghi "Không có trên sàn". Nếu bị chặn CAPTCHA, đợi 5s thử lại (tối đa 3 lần). Agent A/B/C chạy SONG SONG.
```

---

## 3. 📝 Soạn Bộ Hợp Đồng + Phụ Lục Tự Động (Pháp Lý / HR)

**Bài toán:** Tạo hợp đồng lao động + phụ lục thử việc + email thông báo từ 1 lệnh.

```
SUDO PROMPT: SOẠN BỘ HỒ SƠ NHÂN SỰ MỚI TỰ ĐỘNG

👑 [VAI TRÒ]
Bạn là Trợ lý Pháp lý & HR Kỹ thuật số. Thông tin nhân sự mới:
- Họ tên: Trần Văn Bình
- Vị trí: Trưởng nhóm Kinh doanh
- Ngày vào: 01/04/2026
- Lương thử việc: 18,000,000 VNĐ (85% lương chính thức)
- Template: /HR/Template_HopDong.docx

⚙️ [MẠNG LƯỚI ĐA ĐẶC VỤ — MÔ HÌNH VERIFY]

📝 [Agent 1 — Soạn Thảo Viên (Contract Drafter)]
Đọc template. Thay thế tất cả placeholder {{...}} bằng thông tin thực.
Tạo thêm Phụ lục Thử Việc (thời hạn 2 tháng, KPI đánh giá).
Xuất: HopDong_TranVanBinh.docx + PhuLuc_ThuViec.docx

✅ [Agent 2 — Kiểm Soát Viên Pháp Lý (Legal Reviewer)]
Đọc 2 file Agent 1 vừa tạo. Kiểm tra:
- Có đủ điều khoản bắt buộc theo Luật Lao Động 2019 không?
- Thời hạn thử việc có vượt quá 60 ngày không?
- Lương thử việc có đúng >= 85% lương chính thức không?
- Chính tả, định dạng ngày tháng, con số.
Nếu phát hiện lỗi → Liệt kê cụ thể → Gửi lại cho Agent 1 sửa.

✉️ [Agent 3 — Email Thông Báo (Notifier)]
Soạn 2 email:
(a) Email gửi Trần Văn Bình: Chào mừng, lịch onboard tuần đầu, tài liệu cần đọc.
(b) Email gửi Trưởng phòng KD: Thông báo nhân sự mới, ngày bắt đầu, yêu cầu chuẩn bị chỗ ngồi.
Lưu: Email_ChaoMung_Binh.md + Email_ThongBao_TP.md

🚧 [RÀNG BUỘC] Thông tin lương CHỈ ghi trong hợp đồng, KHÔNG ghi trong email. Agent 2 PHẢI kiểm tra trước khi Agent 3 chạy.
```

---

## 4. 📈 Phân Tích Khách Hàng RFM + Email Cá Nhân Hóa (CRM / Marketing)

**Bài toán:** Phân nhóm 5,000 khách theo RFM, soạn email riêng cho từng nhóm.

```
SUDO PROMPT: PHÂN TÍCH RFM & EMAIL CÁ NHÂN HÓA THEO PHÂN KHÚC

👑 [VAI TRÒ]
Bạn là Giám đốc CRM. Mục tiêu: Phân nhóm 5,000 khách hàng theo mô hình RFM, soạn 4 mẫu email cho 4 nhóm.
File: /CRM/LichSu_MuaHang_2025.xlsx (cột: Mã KH, Tên KH, Email, Ngày mua, Số tiền)

⚙️ [MẠNG LƯỚI ĐA ĐẶC VỤ (3 TẦNG)]

📊 [Agent 1 — Nhà Phân Tích RFM (RFM Calculator)]
Đọc file. Tính cho mỗi khách:
- Recency: Số ngày kể từ lần mua cuối đến hôm nay.
- Frequency: Tổng số đơn hàng.
- Monetary: Tổng chi tiêu.
Chấm điểm mỗi chỉ số 1-5 (quintile). Tổng điểm RFM.
Phân nhóm: VIP (R≥4, F≥4, M≥4), Trung Thành (F≥4), Ngủ Đông (R≤2), Mới (F=1).
Xuất file PhanNhom_RFM.xlsx.

✉️ [Agent 2 — Nhà Soạn Email (Campaign Writer)]
Nhận file phân nhóm từ Agent 1. Soạn 4 mẫu email khác nhau:
- VIP: Cảm ơn + ưu đãi độc quyền 20%.
- Trung Thành: Điểm thưởng x2 trong tháng.
- Ngủ Đông: "Chúng tôi nhớ bạn" + coupon quay lại 15%.
- Mới: Hướng dẫn sử dụng + ưu đãi lần 2.
Lưu 4 file: Email_VIP.html, Email_TrungThanh.html, Email_NguDong.html, Email_Moi.html

📄 [Agent 3 — Tổng Kết Dashboard (Summary Builder)]
Tạo báo cáo tổng quan: Số lượng mỗi nhóm, % tổng doanh thu, Top 10 VIP.
Xuất file BaoCao_RFM_TongQuan.xlsx + vẽ biểu đồ tròn phân bổ nhóm (lưu .png).

🚧 [RÀNG BUỘC] Cấm sửa file gốc. Email phải có nút CTA (Call-to-Action). Dữ liệu cá nhân (email, SĐT) chỉ dùng để gửi mail, KHÔNG in ra báo cáo tổng quan.
```

---

## 5. 🏗️ Báo Cáo Tiến Độ Dự Án Xây Dựng (PMO / Giám Đốc Dự Án)

**Bài toán:** Tổng hợp tiến độ từ 5 bảng Gantt khác nhau thành 1 báo cáo CEO.

```
SUDO PROMPT: TỔNG HỢP TIẾN ĐỘ ĐA DỰ ÁN CHO CEO

👑 [VAI TRÒ]
Bạn là PMO Director. Mục tiêu: Đọc 5 file tiến độ dự án, tổng hợp thành 1 báo cáo tình trạng gửi CEO.
Files:
- /DuAn/TienDo_KhoA.xlsx
- /DuAn/TienDo_KhoB.xlsx
- /DuAn/TienDo_NhaXuong.xlsx
- /DuAn/TienDo_VanPhong.xlsx
- /DuAn/TienDo_HaTang.xlsx

⚙️ [MẠNG LƯỚI ĐA ĐẶC VỤ — FAN-OUT + PIPELINE]

📥 [Agent 1A/1B/1C/1D/1E — 5 Thợ Đọc Song Song]
Mỗi Agent đọc 1 file. Trích xuất: Tên hạng mục, % Hoàn thành, Ngày deadline, Trạng thái (Đúng hạn / Trễ / Chưa bắt đầu). Lưu kết quả chuẩn hóa vào /tmp/.

📊 [Agent 2 — Tổng Hợp & Phân Tích (Consolidator)]
Gộp 5 bảng từ Agent 1. Tính: % hoàn thành trung bình toàn dự án. 
Đánh dấu đỏ: Hạng mục trễ > 7 ngày. Đánh dấu vàng: Trễ 1-7 ngày.
Tạo bảng xếp hạng: Dự án nào "khỏe" nhất, dự án nào "nguy" nhất.

📄 [Agent 3 — Báo Cáo CEO (Executive Report)]
Xuất file BaoCao_TienDo_CEO.xlsx:
- Sheet 1: Dashboard tổng quan (bảng + biểu đồ thanh).
- Sheet 2: Danh sách hạng mục TRỄ cần can thiệp.
- Sheet 3: Đề xuất hành động (ưu tiên theo mức độ rủi ro).
Thêm 1 file BaoCao_CEO.md tóm tắt 5 dòng (CEO bận, không đọc dài).

🚧 [RÀNG BUỘC] Cấm sửa file gốc. Nếu file trống hoặc lỗi, ghi "FILE LỖI — Cần kiểm tra thủ công". Agent 1A-1E chạy SONG SONG.
```

---

## 📌 Hướng Dẫn Sử Dụng

1. **Copy** toàn bộ nội dung trong khung code (```) của Prompt bạn muốn.
2. **Mở** [Antigravity](https://antigravity.google) → Panel Chat.
3. **Paste** vào ô chat.
4. **Thay đổi** đường dẫn file (`/Data/...`) cho khớp với thư mục dữ liệu của bạn.
5. **Enter** → Ngồi xem AI điều binh.

> 🔗 Xem thêm lý thuyết Multi-Agent tại [Chương 17 — Điều Binh Đa Đặc Vụ](09-multi-agent.md).
> 🔗 Lưu Prompt hay thành Skill tái sử dụng tại [Chương 17 — Skills & Workflows](07-skills-va-workflows.md).
