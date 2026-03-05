# Chương 8: MCP — Cánh Cổng Kết Nối Antigravity Với Thế Giới Bên Ngoài

> [!IMPORTANT]
> **MCP (Model Context Protocol)** là "linh hồn" của Agentic AI. Nó phá vỡ bức tường ngăn cách giữa trí tuệ nhân tạo và dữ liệu thực tế của doanh nghiệp.

- **🎯 [Mục Tiêu Chương] (Objective):** Xóa bỏ ranh giới "AI bị nhốt trong hộp". Hướng dẫn Sếp cách cấp chìa khóa định tuyến cho Antigravity để nó cắm vòi hút Data trực tiếp từ Google Sheets, MySQL và phát loa qua Slack.
- **📥 [Đầu Vào] (Input):** Một tài khoản Google Workspace hoặc Chuỗi kết nối Database nội bộ (Read-Only).
- **🚀 [Đầu Ra] (Output):** AI truy vấn được doanh thu Real-time trong 5 giây và vẽ biểu đồ ngay trên khung Chat.

---

## 8.2. Mở Đầu: MCP Là Gì? — Giải Mã Bằng Ngôn Ngữ Doanh Nhân

![MCP — Cầu nối Antigravity với Google Sheets, Slack, Database và API nội bộ](images/mcp_protocol.png)

### 📖 Ẩn Dụ Cửa Hàng Tiện Lợi

Hãy tưởng tượng Antigravity là một **Siêu Đầu Bếp** cực kỳ tài năng. Anh ta có thể nấu bất cứ món nào — nhưng anh ta bị nhốt trong một căn bếp nhỏ, chỉ có dao và thớt.

**MCP (Model Context Protocol)** chính là việc **MỞ CỬA CĂN BẾP** cho Đầu Bếp chạy ra ngoài chợ lấy nguyên liệu:

- Kết nối trực tiếp với **Google Sheets** để đọc/ghi dữ liệu.
- Kết nối với **Database MySQL/PostgreSQL** để truy vấn số liệu kinh doanh.
- Kết nối với **Slack/Telegram** để gửi cảnh báo tự động.
- Kết nối với **API bên thứ 3** (KiotViet, Shopee, VNPAY...) để lấy dữ liệu real-time.

**Không có MCP:** AI chỉ đọc được file trên máy tính của bạn.
**Có MCP:** AI có thể chui vào mọi hệ thống doanh nghiệp, đọc dữ liệu sống, ghi kết quả trực tiếp.

> [!NOTE]
> **Gartner 2025:** 88% lãnh đạo C-level phàn nàn AI hiện tại "quá tĩnh". MCP chính là lời giải giúp AI Agent vận hành với tốc độ mili-giây trên dữ liệu sống.

### Định Nghĩa Kỹ Thuật (Dành Cho IT)

**MCP (Model Context Protocol)** là giao thức chuẩn mở do Anthropic phát triển, cho phép AI kết nối với các nguồn dữ liệu và dịch vụ bên ngoài thông qua các MCP Server. Mỗi MCP Server là một chương trình nhỏ đóng vai trò "Cầu nối" giữa AI và một hệ thống cụ thể.

```text
┌─────────────────┐     MCP Protocol     ┌──────────────────┐
│   Antigravity   │ ◄──────────────────►  │   MCP Server     │
│   (AI Agent)    │                       │ (Google Sheets)  │
└─────────────────┘                       └──────────────────┘
                                                    │
                                                    ▼
                                          ┌──────────────────┐
                                          │  Google Sheets    │
                                          │  (Dữ liệu sống) │
                                          └──────────────────┘
```

---

## 8.3. [Phương Pháp Cốt Lõi] Cách Cài Đặt MCP Trong Antigravity — Hướng Dẫn Từng Bước

### Bước 1: Tạo File Cấu Hình MCP

Tạo file `.gemini/settings.json` trong thư mục HOME của bạn:

```json
{
  "mcpServers": {
    "google-sheets": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-server-google-sheets"],
      "env": {
        "GOOGLE_SHEETS_API_KEY": "YOUR_API_KEY_HERE"
      }
    },
    "mysql_database": {
      "command": "npx", 
      "args": ["-y", "@anthropic/mcp-server-mysql"],
      "env": {
        "DATABASE_URL": "mysql://user:pass@localhost:3306/SME_Biz_Data"
      }
    },
    "slack": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-server-slack"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-YOUR-TOKEN"
      }
    }
  }
}
```

### 👣 Quy trình 3 bước "Xuyên không" vào Database doanh nghiệp

1. **Khởi tạo:** Tạo file `.gemini/settings.json` trong thư mục Home để khai báo các Server MCP cần dùng (Google Sheets, MySQL...).
2. **Cấp quyền (Permission):**
   - 🛡️ **Google Sheets:** Share quyền Editor cho email Service Account của robot.
   - 🛡️ **MySQL:** Cấp tài khoản `ReadOnly` để AI chỉ được xem, không được xóa dữ liệu.
3. **Kích hoạt:** Khởi động lại Antigravity và gõ: *"Hãy liệt kê tất cả MCP resources đang kết nối."*

### Bước 2: Khởi Động Lại Antigravity

Sau khi lưu file, khởi động lại Antigravity. Nó sẽ tự động nhận diện và kết nối với các MCP Server đã cấu hình.

### Bước 3: Kiểm Tra Kết Nối

Gõ vào Antigravity:
> *"Hãy liệt kê tất cả MCP resources mà bạn đang kết nối."*

AI sẽ trả về danh sách các MCP Server và tài nguyên có sẵn.

### ✅ Expected Output

```text
Đã kết nối 3 MCP Servers:
1. google-sheets: Đọc/Ghi Google Sheets (5 spreadsheets có sẵn)
2. database: Truy vấn PostgreSQL (12 bảng trong schema public)
3. slack: Gửi tin nhắn Slack (3 channels)
```

---

## 8.4. [Ví Dụ Mẫu & Case Study] Case Study Ứng Dụng MCP Trong Doanh Nghiệp

### 💼 Case Study 1: Kế Toán — Đối Soát COD Real-Time Với Google Sheets

**Bối cảnh:** Thay vì export file CSV từ KiotViet rồi copy vào thư mục mỗi cuối tháng, Kế toán muốn AI tự động đọc dữ liệu sống từ Google Sheets (được sync tự động từ KiotViet).

**Cấu hình MCP:**

```json
{
  "mcpServers": {
    "kiotviet-sheets": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-server-google-sheets"],
      "env": {
        "GOOGLE_SHEETS_API_KEY": "AIza..."
      }
    }
  }
}
```

**Sudo Prompt Với MCP:**

> **SUDO PROMPT: ĐỐI SOÁT COD REAL-TIME QUA MCP**
>
> 👑 **[VAI TRÒ]** Kế toán trưởng kiểm toán nội bộ.
>
> ⚙️ **[TIẾN TRÌNH]**
>
> 1. Dùng `list_resources` để liệt kê các Google Sheets đang kết nối.
> 2. Dùng `read_resource` đọc Sheet "DoanhThu_Thang10" (file nội bộ KiotViet).
> 3. Dùng `read_resource` đọc Sheet "SaoKe_GHTK_T10" (file đối tác).
> 4. Clean data: Trim SĐT, chuẩn hóa +84→0, ép tiền về Float.
> 5. Merge outer trên cột Mã Vận Đơn. Phân 3 nhóm: Thất thoát, Đơn ảo, Chênh lệch.
> 6. Ghi kết quả vào Sheet mới "KetQua_DoiSoat_T10" trên Google Sheets.
> 7. Gửi thông báo qua Slack channel #ketoan: "🚨 Phát hiện X đơn bất thường."

**Tiến Trình Thực Thi Trực Tiếp Trên Giao Diện Antigravity:**

Đừng nghĩ cấu hình MCP là thứ gì đó cao siêu của Coder. Hãy xem những gì chị Kế toán trải nghiệm:

1. **Gắn Cáp Vào Database Sống:** Bạn mở Antigravity, lập tức nhìn thấy một thẻ trạng thái màu xanh lá cây ✅ báo hiệu `Integration Status: Active (Connected to Google Sheets via MCP)`.
2. **Kích Hoạt Nhãn Quan Toán Học:** Bạn Paste lệnh Sudo Prompt thẳng vào khung Chat. Antigravity tự động luồn lách qua hệ bảo mật, vào đọc 10.000 dòng Excel trực tiếp trên Google Workspace mà không yêu cầu bạn tải bất kỳ File `.xlsx` nào về máy local.
3. **Hiển Thị Bảng Lọc Tĩnh Lặng:** Chatbot phản hồi lại Bức tranh Dữ liệu bằng một Bảng Data (Mini Table) hiển thị ngay trên tin nhắn Chat, soi rọi chính xác 89 dòng lệch được tô màu Đỏ báo động.

![Giao diện Antigravity kết nối trực tiếp với Google Sheets qua MCP và hiển thị kết quả kiểm toán Data Sống](images/mcp_google_sheets_ui.png)

**Kết Quả Căn Cốt Của Thời Đại Mới:**
Kế toán không cần thao tác Export/Import file thủ công lặp đi lặp lại mỗi ngày. Mọi thứ diễn ra trên Data Sống. Sếp mở điện thoại xem Sheet gốc của Google là tự thấy Output hiển thị. Lỗ hổng thời gian (Time-lag) của doanh nghiệp bằng 0.

---

### 💼 Case Study 2: Sales — Bức Tranh Doanh Thu Real-Time Từ Máy Chủ MySQL Mù Chữ SQL

**Bối cảnh:** Giám đốc Kinh doanh (Sếp Nam) đang ngồi trong phòng họp rà soát KQKD Quý 3. Ở thập kỷ trước, Sếp Nam sẽ phải gọi điện: *"Phòng IT đâu, viết cho anh câu lệnh SQL (Truy vấn Cơ sở dữ liệu) xuất Doanh thu Từng Đại Lý lên màn hình đi."* IT mất 1 tiếng rưỡi xin quyền để chạy Report mệt mỏi.

Cỗ máy MySQL (hoặc Postgres) chứa hàng Triệu giao dịch. Sếp Nam Mù Chữ SQL. Không sao cả, Antigravity làm Phiên Dịch Viên MCP:

**Sudo Prompt Cắm Thẳng Vào Van Database Tim Mạch Công Ty:**

> **SUDO PROMPT: LỆNH XUẤT ĐỒ THỊ DOANH THU ĐỘNG CẬP NHẬT TỪNG LI**
>
> 👑 **[VAI TRÒ]** Trưởng phòng phân tích kinh doanh (Data Analyst).
>
> ⚙️ **[TIẾN TRÌNH THỰC THI KHÔNG CHẠM CODE CỦA CEO]**
>
> 1. Gọi MCP Server `mysql_database` truy cập thẳng Mạch máu.
> 2. Hãy tự suy luận câu Lệnh SQL (Sếp không biết code): Kéo tất cả Doanh Thu bán hàng Ngày Hôm Nay. Group (Nhóm) lại theo `product_name`. Xếp hạng Tổng tiền từ Lớn Xuống Bé.
> 3. Cấm in ra dữ liệu Bảng Số (Rác mắt). Dùng Trình Hiển Thị Terminal Vẽ Luôn Cho Tôi 1 Cái Chart Biểu Đồ Cột Trực Tiếp (Hoặc Lưu ra `Bieu_do_DoanhThu.png`).
> 4. Gửi Phi Tiêu Biểu đồ Đẹp Mắt Đó Vào Slack Channel #Sales_Vip cho anh em ngợp!

**Kết quả kỳ vọng (Phép Thuật Của Ngôn Ngữ Tự Nhiên):**

Trong 5 giây, AI (không cần ai code) Tự Gõ Lệnh SQL vào Lõi Máy Chủ: `SELECT product_name, SUM(amount)...`. Và Màn Hình Của Sếp Nam Nảy Lên Một Bức Tranh Biểu Đồ Màu Sắc rực rỡ.

> *"Đã luồn lệnh thành công vào `mysql_database` (Duyệt qua 1.247 giao dịch Real-time). Sản Phẩm Bán Đỉnh Nhất Đang Chạy Là Màn Hình LG (67 đơn, 5.4 tỷ). Đồ thị Visualization đã được nhúng thẳng vào Giao Diện Chat này. Đã Phi báo cáo vào #Sales_Vip."*

**Không cần học IT, Không Cần PowerBI Đắt Đỏ. Bắt SQL Phục vụ Bằng Tiếng Việt.**

---

### 💼 Case Study 3: HR — Tự Động Onboard Nhân Viên Mới Đa Hệ Thống

**Bối cảnh:** Khi nhân viên mới ký hợp đồng, HR phải tạo tài khoản ở 5 nơi: Email công ty, Slack, KiotViet, Google Drive, Bảng chấm công. Với MCP, AI làm hết.

**Sudo Prompt Với MCP:**

> **SUDO PROMPT: TỰ ĐỘNG ONBOARD NHÂN VIÊN MỚI**
>
> 👑 **[VAI TRÒ]** Quản lý hệ thống nhân sự tự động.
>
> ⚙️ **[TIẾN TRÌNH]**
>
> 1. Đọc file `/HR/NhanVien_Moi.xlsx` lấy thông tin: Họ Tên, Email cá nhân, Phòng ban, Chức vụ.
> 2. Dùng MCP Server `slack`: Mời nhân viên vào Workspace Slack, thêm vào channel phòng ban.
> 3. Dùng MCP Server `google-sheets`: Thêm 1 dòng mới vào Sheet "BangChamCong_2025" với thông tin nhân viên.
> 4. Dùng MCP Server `database`: INSERT vào bảng `employees` trong PostgreSQL.
> 5. Soạn email chào mừng gửi đến email cá nhân nhân viên (kèm link tài liệu nội bộ).
> 6. In checklist hoàn thành: ✅ Slack, ✅ Chấm công, ✅ Database, ✅ Email.

---

### 💼 Case Study 4: Data Analyst — Điều Khiển Dashboard BI (Metabase/Superset) Bằng Giọng Nói

**Bối cảnh:** Bạn đã xây xong Data Warehouse ở Chương 6. Bạn cắm Metabase vào để vẽ Biểu đồ. Tuy nhiên, hàng tuần Sếp lại yêu cầu: *"Tạo cho anh 1 cái Dashboard mới chỉ track riêng khu vực Đà Nẵng, gửi Link cho anh trước 9h sáng"*. Phải mất 30 phút kéo thả trên Metabase.

Dùng MCP, Antigravity thao túng trực tiếp Metabase API:

**Sudo Prompt Cắm Thẳng Vào Van Metabase:**

> **SUDO PROMPT: KIẾN TRÚC SƯ BI DASHBOARD TỐC ĐỘ ÁNH SÁNG**
>
> 👑 **[VAI TRÒ]** Giám đốc Trí Tuệ Doanh Nghiệp (BI Director).
>
> ⚙️ **[TIẾN TRÌNH]**
>
> 1. Gọi MCP Server `metabase_api`. Nhận diện các Collections hiện có.
> 2. Khởi tạo 1 Question mới (Query SQL trích xuất Data từ Table `fct_doanh_thu` chỉ lấy `region = 'Đà Nẵng'`).
> 3. Đóng gói Question đó thành 1 cái Dashboard mới Đặt tên là "Giám Sát Vùng Đà Nẵng - Realtime".
> 4. Xuất Public Link của Dashboard đó ra đây cho Sếp.
> 5. Dùng MCP `slack` gửi Link đó vào Channel #BOD_DaNang với lời chào: "Mời các Sếp thưởng lãm số liệu sáng nay!"

**Mọi thứ diễn ra tự động. AI tự sinh Link Dashboard và gửi đi thay vì Human phải bấm trỏ chuột.**

> [!TIP]
> **Dòng Tiền đến từ đâu?** Giải phóng IT khỏi các việc "Sếp ơi kéo báo cáo". CEO tự đọc số sáng sớm không cần chờ nhân viên đến văn phòng. Tốc độ ra quyết định (Speed of Decision) tăng gấp 10 lần.

---

## 8.6. [Kết Quả Đầu Ra & Processing] Danh Sách MCP Server Phổ Biến Cho Doanh Nghiệp Việt

| MCP Server | Mục đích | Phòng ban |
| :--- | :--- | :--- |
| `mcp-server-google-sheets` | Đọc/Ghi Google Sheets | Kế toán, Sales, HR |
| `mcp-server-postgres` / `mysql` | Truy vấn Database | IT, Ban GĐ |
| `mcp-server-slack` | Gửi tin nhắn/cảnh báo Slack | Tất cả |
| `mcp-server-filesystem` | Đọc/Ghi file trên server | IT, Kế toán |
| `mcp-server-github` | Quản lý code, tạo PR, review | IT/DevOps |
| `mcp-server-brave-search` | Tìm kiếm web | Marketing, Sales |
| `mcp-server-puppeteer` | Điều khiển trình duyệt | Sales (cào data) |
| `mcp-server-memory` | Lưu trữ trí nhớ dài hạn AI | Tất cả |

---

## 8.5. [Cách Làm Chi Tiết & Hướng Dẫn Kỹ Thuật] Quy Trình Tích Hợp MCP Cho SME (Step-by-Step)

### Giai đoạn 1: Khảo sát (Ngày 1-2)

1. Liệt kê tất cả hệ thống doanh nghiệp đang dùng (KiotViet, Google Sheets, Slack, Database...).
2. Xác định 3 "Điểm đau" lớn nhất cần kết nối (VD: Kế toán phải export file thủ công).
3. Kiểm tra xem hệ thống đó có API không (hầu hết đều có).

### Giai đoạn 2: Cài đặt MCP Server (Ngày 3-5)

1. Cài Node.js (xem [Phụ lục](phu-luc-cai-dat-moi-truong.md)).
2. Tạo file `.gemini/settings.json` với cấu hình MCP Server.
3. Lấy API Key/Token từ các hệ thống (Google Cloud Console, Slack Admin...).
4. Test kết nối bằng lệnh `list_resources`.

### Giai đoạn 3: Xây Prompt & Workflow (Ngày 6-10)

1. Viết Sudo Prompt sử dụng các tool MCP (`list_resources`, `read_resource`).
2. Tạo Workflow `.md` gọi MCP (đính `// turbo-all` nếu đã test an toàn).
3. Test trên dữ liệu sandbox trước khi chạy production.

### Giai đoạn 4: Mở rộng & Giám sát (Ngày 11+)

1. Thêm MCP Server cho các hệ thống khác.
2. Đặt Cronjob chạy Workflow MCP tự động (VD: 8h sáng thứ 2 hàng tuần).
3. Thiết lập cảnh báo qua Slack/Telegram khi có bất thường.

---

### Troubleshooting MCP

| Sự Cố | Nguyên Nhân | Giải Pháp |
| :--- | :--- | :--- |
| `MCP Server not found` | Chưa cài Node.js hoặc npx | Chạy: `brew install node` (macOS) hoặc xem [Phụ lục](phu-luc-cai-dat-moi-truong.md) |
| `Authentication failed` | API Key/Token hết hạn hoặc sai | Kiểm tra lại Key trong file `settings.json`. Tạo Key mới nếu cần. |
| `Permission denied` khi đọc Sheet | Chưa share Sheet cho Service Account | Share Google Sheet cho email Service Account với quyền Viewer/Editor. |
| `Connection refused` khi kết nối DB | Database chưa cho phép kết nối từ bên ngoài | Thêm IP máy vào whitelist DB. Kiểm tra firewall. |
| MCP Server chạy chậm | Server MCP bị timeout do dữ liệu quá lớn | Giới hạn query: thêm `LIMIT 1000` vào SQL. Chia nhỏ request. |

---

## 8.7. [Kết Luận & Action Items] Tổng Kết & Tài Liệu Tham Khảo

- [Model Context Protocol — Tài liệu chính thức](https://modelcontextprotocol.io/)
- [Danh sách MCP Servers có sẵn](https://github.com/modelcontextprotocol/servers)
- [Hướng dẫn tạo MCP Server tùy chỉnh](https://modelcontextprotocol.io/docs/concepts/servers)
- [Chương 0 — Giới thiệu Antigravity](00-gioi-thieu-antigravity.md)
- [Chương 7 — Skills & Workflows](07-skills-va-workflows.md)
- [Chương 16 — Bảo Mật & Quyền Riêng Tư](16-bao-mat-phap-ly.md)
