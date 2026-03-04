# Chương Chuyên Sâu: Kho Vũ Khí Bí Mật - Cách Sử Dụng "Skills" Và "Workflows" Trong Antigravity

## 1. Mở Đầu: Tại Sao Bạn Đang Sử Dụng AI Chỉ Ở 10% Công Suất?

Hầu hết người dùng Antigravity (kể cả dân IT lâu năm) đang mắc một sai lầm giống nhau: Mỗi lần mở thanh Chat lên, họ lại gõ lại từ đầu toàn bộ yêu cầu. Hôm nay gõ: *"Hãy tạo báo cáo doanh thu tháng 4"*. Ngày mai lại gõ: *"Hãy tạo báo cáo doanh thu tháng 5"* - câu lệnh y hệt, chỉ sửa con số 4 thành 5, mà phải gõ lại từ A đến Z.

Đó giống như bạn có một nhà máy hiện đại, nhưng mỗi sáng lại phải dạy lại công nhân cách vặn ốc từ đầu. Lãng phí kinh khủng!

**Antigravity sở hữu 2 Hệ thống "Trí Nhớ Cơ Bắp" (Muscle Memory) giúp nó "Nhớ" cách làm việc mà không cần bạn dạy lại:**

1. **Skills (Kỹ Năng):** Là những "Cuốn Sổ Tay Nghiệp Vụ" được viết sẵn. Khi AI cần làm một việc phức tạp (ví dụ: Deploy Server, Phân tích SEO, Tạo Dashboard), nó sẽ tự mở Sổ Tay đó ra đọc hướng dẫn rồi làm theo y hệt.
2. **Workflows (Quy Trình):** Là những "Công Thức Nấu Ăn" (Recipe) được bạn viết sẵn. Mỗi khi bạn gõ một Lệnh Tắt (Slash Command) như `/bao_cao_thang`, AI tự động chạy nguyên cái công thức đó mà không cần bạn nhắc lại từng bước.

Hãy tưởng tượng: Thay vì mỗi sáng phải viết 1 trang A4 để giao việc cho nhân viên, bạn chỉ cần vỗ vai và nói: **"Làm theo Quy Trình Số 7 đi em!"** - Nhân viên AI lập tức hiểu phải làm gì, dùng công cụ nào, và lưu kết quả ở đâu.

Chương này sẽ hướng dẫn bạn Khai Phá 2 Hệ Thống Trí Nhớ này một cách triệt để.

---

## 2. SKILLS (Kỹ Năng): Cuốn Sổ Tay Nghiệp Vụ Của AI

### 2.1. Skills Là Gì? (Giải Thích Cho Dân Business)

Hãy nghĩ về Skills như thế này: Khi bạn tuyển một nhân viên mới vào phòng Kế Toán, bạn sẽ đưa cho họ một **"Cẩm Nang Onboarding" (Sổ Tay Nhập Môn)** ghi rõ:

- Bước 1: Mỗi sáng mở file Excel ở thư mục A.
- Bước 2: Kiểm tra cột B có dữ liệu mới không.
- Bước 3: Nếu có, chạy hàm VLOOKUP đối chiếu với file C.
- Bước 4: Lưu kết quả vào thư mục D.

Sau khi đọc xong, nhân viên biết phải làm gì mà không cần bạn kè kè bên cạnh.

**Skills trong Antigravity hoạt động y hệt vậy.** Một Skill là một thư mục chứa ít nhất 1 file `SKILL.md` – đây chính là "Cuốn Sổ Tay" hướng dẫn AI cách thực hiện một nghiệp vụ chuyên biệt. Khi AI gặp một bài toán phù hợp, nó sẽ tự động mở file `SKILL.md` ra đọc, rồi thực hiện từng bước theo đúng hướng dẫn.

### 2.2. Cấu Trúc Của 1 Skill (Bên Trong Cuốn Sổ Tay Gồm Những Gì?)

Một Skill không chỉ là 1 file chữ suông. Nó có thể là cả một "Bộ Dụng Cụ Nghề" hoàn chỉnh:

```
📁 skills/
 └── 📁 bao_cao_doanh_thu/          ← Tên Kỹ năng
      ├── 📄 SKILL.md                ← Sổ Tay Chính (Bắt buộc có)
      ├── 📁 scripts/                ← Các file code phụ trợ
      │    └── 📄 tinh_tong.py       ← Script Python tính toán
      ├── 📁 examples/               ← Mẫu tham khảo 
      │    └── 📄 bao_cao_mau.xlsx   ← File Excel mẫu
      └── 📁 resources/              ← Tài nguyên bổ sung
           └── 📄 template_bieu_do.json  ← Mẫu biểu đồ
```

### 2.3. File SKILL.md Viết Như Thế Nào? (Guideline Cầm Tay Chỉ Việc)

Đây là phần quan trọng nhất. File `SKILL.md` dùng Định dạng YAML Frontmatter (Phần đầu trang có gạch `---`) kết hợp với Markdown (Phần thân nội dung). Cấu trúc chuẩn của một `SKILL.md` gồm:

```markdown
---
name: Báo Cáo Doanh Thu Tháng
description: Kỹ năng tự động đọc file Excel doanh thu, tính tổng theo chi nhánh, và xuất biểu đồ cột.
---

# Hướng Dẫn Thực Hiện

## Bối Cảnh
Skill này được kích hoạt khi người dùng yêu cầu tạo báo cáo doanh thu hàng tháng.
Dữ liệu nguồn nằm tại thư mục `/Data/DoanhThu/`.

## Quy Trình Từng Bước

### Bước 1: Thu Thập Dữ Liệu
- Dùng công cụ `list_dir` quét thư mục `/Data/DoanhThu/` để tìm tất cả file .xlsx trong tháng hiện tại.
- Dùng `view_file` đọc lướt dòng đầu tiên (Header) để xác nhận cấu trúc cột.

### Bước 2: Xử Lý & Tổng Hợp
- Viết script Python sử dụng Pandas:
  - Đọc tất cả file Excel tìm được.
  - Gộp (Concatenate) thành 1 DataFrame duy nhất.
  - Nhóm theo cột "Chi Nhánh", tính Tổng cột "Doanh Thu".

### Bước 3: Trực Quan Hóa
- Dùng Matplotlib vẽ biểu đồ cột (Bar Chart).
- Cột nào có Doanh thu giảm > 20% so với tháng trước → Tô màu Đỏ cảnh báo.
- Lưu ảnh biểu đồ tại `/Output/bao_cao_thang_X.png`.

### Bước 4: Báo Cáo
- Thông báo cho người dùng kết quả bằng `notify_user`.
- Đính kèm file ảnh biểu đồ và bảng tóm tắt top 3 chi nhánh tốt nhất / kém nhất.

## Lưu Ý Quan Trọng
- KHÔNG được xóa hoặc sửa đổi file dữ liệu gốc.
- Nếu file Excel bị lỗi format, bỏ qua file đó và ghi nhận vào danh sách "File Lỗi".
```

### 2.4. Ứng Dụng Thực Tế: Tạo Bộ Skills Riêng Cho Phòng Ban

Giá trị thực sự của Skills nằm ở chỗ: **Bạn xây một lần, dùng mãi mãi.**

Hãy tưởng tượng bạn là Giám đốc một công ty có 4 phòng ban. Bạn sẽ yêu cầu Antigravity tạo cho mình 4 Bộ Kỹ năng:

| Phòng Ban | Tên Skill | Mô Tả |
|:---|:---|:---|
| **Kế Toán** | `doi_soat_ngan_hang` | Đọc 2 file (Sổ kế toán + Sao kê NH), đối chiếu chéo, xuất báo cáo lệch |
| **HR** | `loc_cv_ung_vien` | Quét thư mục CV, chấm điểm theo JD, phân loại Đạt/Không Đạt |
| **Marketing** | `phan_tich_doi_thu` | Mở browser cào giá đối thủ trên Shopee, so sánh với giá mình |
| **Kinh Doanh** | `tao_bao_gia_tu_dong` | Đọc danh sách sản phẩm, áp giá theo khung chiết khấu, xuất PDF báo giá |

Khi Kế Toán cần đối soát, họ không cần viết Prompt dài 2 trang. Antigravity tự nhận ra bài toán khớp với Skill `doi_soat_ngan_hang`, tự mở file `SKILL.md` ra đọc, và thực hiện đúng quy trình.

> **SUDO PROMPT (Mẫu Yêu Cầu AI Tạo Skill Mới Cho Bạn):**
>
> *"Antigravity, hãy tạo cho tôi 1 Skill mới tên là `doi_soat_ngan_hang` trong thư mục `skills/`. File SKILL.md phải mô tả chi tiết quy trình: Bước 1 đọc file Sổ Kế Toán nội bộ, Bước 2 đọc file Sao Kê Ngân Hàng BIDV, Bước 3 dùng Pandas merge đối chiếu theo cột Mã Giao Dịch, Bước 4 xuất báo cáo chênh lệch ra Excel có tô màu đỏ. Ngoài ra, tạo thêm thư mục `examples/` chứa 1 file mẫu `sao_ke_mau.csv` với 10 dòng dữ liệu giả để tôi test. Tạo ngay!"*

---

## 3. WORKFLOWS (Quy Trình): Công Thức Nấu Ăn "Một Chạm"

### 3.1. Workflows Là Gì? (Giải Thích Cho Dân Business)

Nếu Skills là "Sổ Tay Nghiệp Vụ" mà AI tự tra cứu khi cần, thì Workflows là "Nút Bấm Tắt" mà BẠN chủ động nhấn khi muốn.

Hãy nghĩ về Workflows như việc bạn lập trình một cái Nút Bấm trên Điều Khiển Từ Xa (Remote Control) của Tivi:

- Bình thường, để xem phim, bạn phải: Bật Tivi → Chuyển sang HDMI 2 → Mở App Netflix → Gõ tìm phim → Nhấn Play. (5 bước)
- Nhưng nếu bạn lập trình 1 Nút: **"Xem Phim"** → Tivi tự làm cả 5 bước trên chỉ với 1 lần bấm.

Trong Antigravity, Workflows được lưu trữ dưới dạng file `.md` trong thư mục `.agents/workflows/`. Mỗi file là một "Công Thức" (Recipe). Bạn kích hoạt nó bằng **Lệnh Gạch Chéo (Slash Command)**: Gõ `/tên_workflow` là AI tự động chạy.

### 3.2. Cấu Trúc Của 1 Workflow (Viết Công Thức Như Thế Nào?)

Một file Workflow dùng YAML Frontmatter cho phần mô tả, và Markdown cho phần hướng dẫn chi tiết:

```markdown
---
description: Tự động deploy ứng dụng Frontend lên Server Staging
---

# Quy Trình Deploy Frontend

## Các Bước Thực Hiện

// turbo-all

1. Kiểm tra nhánh Git hiện tại:
   Chạy lệnh: `git status` để xác nhận đang ở nhánh `dev`.

2. Kéo code mới nhất từ Remote:
   Chạy lệnh: `git pull origin dev`

3. Cài đặt lại Dependencies:
   Chạy lệnh: `npm install --silent`

4. Build bản Production:
   Chạy lệnh: `npm run build`

5. Copy thành phẩm lên Server:
   Chạy lệnh: `scp -r ./build user@server:/var/www/app/`

6. Khởi động lại Web Server:
   Chạy lệnh: `ssh user@server "sudo systemctl reload nginx"`

7. Kiểm tra Website hoạt động:
   Mở browser kiểm tra `https://staging.company.com` trả về status 200.
```

### 3.3. Giải Mã Các "Phép Thuật" Đặc Biệt Trong Workflow

Có 2 câu thần chú (Annotation) cực kỳ quan trọng mà dân Business cần biết:

**`// turbo`** (Đặt trước 1 bước duy nhất):

- Ý nghĩa: "Bước này AN TOÀN, cứ tự động chạy đi, không cần hỏi tôi."
- Ví dụ: Lệnh `git status` chỉ XEM trạng thái, không thay đổi gì → An toàn → Gắn `// turbo`.

**`// turbo-all`** (Đặt ở bất kỳ đâu trong file):

- Ý nghĩa: "TẤT CẢ các bước trong Workflow này đều AN TOÀN. Chạy hết tự động, không cần hỏi ý kiến tôi bước nào."
- Khi nào dùng: Khi bạn đã test kỹ quy trình nhiều lần và chắc chắn không có rủi ro.

**Nếu không có `// turbo`:** AI sẽ dừng lại ở MỖI bước và hỏi bạn: *"Sếp ơi, em có nên chạy lệnh này không?"* → An toàn nhưng chậm.

### 3.4. Guideline Thực Chiến: Xây Dựng Bộ Workflows Cho Doanh Nghiệp

Dưới đây là Bảng Thiết Kế Mẫu cho một doanh nghiệp muốn "Điều khiển từ xa" toàn bộ hoạt động bằng Slash Commands:

| Slash Command | File Workflow | Chức Năng |
|:---|:---|:---|
| `/bao_cao_sang` | `bao_cao_sang.md` | 8h sáng: Đọc file doanh thu hôm qua → Vẽ biểu đồ → Gửi Telegram cho Sếp |
| `/doi_soat` | `doi_soat_cuoi_thang.md` | Đọc 2 file Excel Kế toán vs Ngân hàng → Tìm lệch → Xuất báo cáo |
| `/loc_cv` | `loc_cv_ung_vien.md` | Quét 300 CV → Chấm điểm → Phân loại vào thư mục Đạt/Không Đạt |
| `/gia_doi_thu` | `crawl_gia_doi_thu.md` | Mở Browser cào giá 50 sản phẩm trên Shopee → Lưu CSV |
| `/deploy` | `deploy_staging.md` | Kéo code mới → Build → Đẩy lên Server → Kiểm tra hoạt động |

> **SUDO PROMPT (Mẫu Yêu Cầu AI Tạo Workflow Mới):**
>
> *"Antigravity, tạo cho tôi 1 Workflow mới. Lưu tại `.agents/workflows/bao_cao_sang.md`.*
> *Mô tả: Báo cáo doanh thu buổi sáng tự động.*
> *Các bước thực hiện:*
> *1. Đọc file `/Data/doanh_thu_hom_qua.xlsx` bằng Python Pandas.*
> *2. Tính tổng doanh thu theo từng chi nhánh.*
> *3. Vẽ biểu đồ cột bằng Matplotlib, lưu ảnh `/tmp/bao_cao.png`.*
> *4. Gửi ảnh đó qua Telegram Bot API kèm dòng chữ tóm tắt.*
> *Đánh dấu `// turbo-all` vì tôi muốn toàn bộ quy trình chạy tự động không hỏi.*
> *Tạo file ngay!"*

---

## 4. Skills vs Workflows: Khi Nào Dùng Cái Nào?

Nhiều người nhầm lẫn giữa Skills và Workflows. Đây là bảng so sánh giúp bạn quyết định:

| Tiêu Chí | Skills | Workflows |
|:---|:---|:---|
| **AI tự kích hoạt?** | ✅ Có - AI tự nhận ra khi nào cần dùng | ❌ Không - Bạn phải gõ Slash Command |
| **Ai viết?** | Bạn hoặc Cộng đồng chia sẻ | Bạn tự viết cho công ty mình |
| **Phù hợp cho?** | Nghiệp vụ phức tạp, cần linh hoạt | Quy trình cố định, lặp đi lặp lại |
| **Ví dụ** | Phân tích dữ liệu tài chính | Deploy Server mỗi thứ 6 |
| **Độ tự do của AI** | Cao - AI có thể sáng tạo thêm | Thấp - AI chạy đúng từng bước |

**Quy tắc vàng:**

- Dùng **Skills** khi bạn muốn AI "Thông minh" – tự biết khi nào cần áp dụng, có thể linh hoạt điều chỉnh.
- Dùng **Workflows** khi bạn muốn AI "Chính xác" – chạy đúng 100% quy trình, không thêm bớt gì.

---

## 5. Tổng Kết: Biến Antigravity Thành "Nhà Máy Có Ký Ức"

Khi bạn xây xong Bộ Skills và Bộ Workflows cho doanh nghiệp, Antigravity không còn là một "Con Robot Mất Trí Nhớ" phải dạy lại mỗi sáng. Nó trở thành một **Nhà Máy Sản Xuất Tự Động có Bộ Nhớ Cơ Bắp (Muscle Memory)**.

Mỗi nhân viên mới vào công ty chỉ cần học thuộc vài Slash Commands: `/bao_cao`, `/doi_soat`, `/deploy`. Không cần 3 tháng Đào tạo. Toàn bộ "Trí khôn tổ chức" (Organizational Intelligence) đã được mã hóa vào các file `.md` nằm gọn gàng trong thư mục `.agents/`.

Đó là sức mạnh thực sự của việc "Làm Chủ Antigravity" – không phải gõ nhanh hơn, mà là **Xây hệ thống một lần, Thu hoạch mãi mãi.**

*(Mời Sếp sang Chương tiếp theo để tìm hiểu cách Bảo vệ toàn bộ Cỗ máy Kinh Doanh này khỏi Rò rỉ Dữ liệu và Tấn công Prompt Injection.)*
