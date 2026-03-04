# Chương 7B: MCP — Cánh Cổng Kết Nối Antigravity Với Thế Giới Bên Ngoài

*(Model Context Protocol — Bí Mật Vũ Khí Mở Rộng Siêu Năng Lực AI)*

---

## 1. MCP Là Gì? — Giải Mã Bằng Ngôn Ngữ Doanh Nhân

### 📖 Ẩn Dụ Cửa Hàng Tiện Lợi

Hãy tưởng tượng Antigravity là một **Siêu Đầu Bếp** cực kỳ tài năng. Anh ta có thể nấu bất cứ món nào — nhưng anh ta bị nhốt trong một căn bếp nhỏ, chỉ có dao và thớt.

**MCP (Model Context Protocol)** chính là việc **MỞ CỬA CĂN BẾP** cho Đầu Bếp chạy ra ngoài chợ lấy nguyên liệu:

- Kết nối trực tiếp với **Google Sheets** để đọc/ghi dữ liệu.
- Kết nối với **Database MySQL/PostgreSQL** để truy vấn số liệu kinh doanh.
- Kết nối với **Slack/Telegram** để gửi cảnh báo tự động.
- Kết nối với **API bên thứ 3** (KiotViet, Shopee, VNPAY...) để lấy dữ liệu real-time.

**Không có MCP:** AI chỉ đọc được file trên máy tính của bạn.
**Có MCP:** AI có thể chui vào mọi hệ thống doanh nghiệp, đọc dữ liệu sống, ghi kết quả trực tiếp.

### Định Nghĩa Kỹ Thuật (Dành Cho IT)

**MCP (Model Context Protocol)** là giao thức chuẩn mở do Anthropic phát triển, cho phép AI kết nối với các nguồn dữ liệu và dịch vụ bên ngoài thông qua các MCP Server. Mỗi MCP Server là một chương trình nhỏ đóng vai trò "Cầu nối" giữa AI và một hệ thống cụ thể.

```
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

## 2. Cách Cài Đặt MCP Trong Antigravity — Hướng Dẫn Từng Bước

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
    "database": {
      "command": "npx", 
      "args": ["-y", "@anthropic/mcp-server-postgres"],
      "env": {
        "DATABASE_URL": "postgresql://user:pass@localhost:5432/mydb"
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

### Bước 2: Khởi Động Lại Antigravity

Sau khi lưu file, khởi động lại Antigravity. Nó sẽ tự động nhận diện và kết nối với các MCP Server đã cấu hình.

### Bước 3: Kiểm Tra Kết Nối

Gõ vào Antigravity:
> *"Hãy liệt kê tất cả MCP resources mà bạn đang kết nối."*

AI sẽ trả về danh sách các MCP Server và tài nguyên có sẵn.

### ✅ Expected Output

```
Đã kết nối 3 MCP Servers:
1. google-sheets: Đọc/Ghi Google Sheets (5 spreadsheets có sẵn)
2. database: Truy vấn PostgreSQL (12 bảng trong schema public)
3. slack: Gửi tin nhắn Slack (3 channels)
```

---

## 3. Case Study Ứng Dụng MCP Trong Doanh Nghiệp

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

**Kết quả:** Kế toán không cần export/import file. Mọi thứ diễn ra trên Google Sheets sống. Sếp mở điện thoại xem Sheet là thấy kết quả.

---

### 💼 Case Study 2: Sales — Dashboard Doanh Thu Real-Time Từ Database

**Bối cảnh:** Giám đốc Sales muốn xem doanh thu theo giờ mà không cần gọi kế toán. Database PostgreSQL của công ty đã lưu mọi giao dịch.

**Sudo Prompt Với MCP:**

> **SUDO PROMPT: BÁO CÁO DOANH THU REAL-TIME**
>
> 👑 **[VAI TRÒ]** Trưởng phòng phân tích kinh doanh.
>
> ⚙️ **[TIẾN TRÌNH]**
>
> 1. Kết nối MCP Server `database`. Liệt kê các bảng trong schema.
> 2. Truy vấn SQL: `SELECT product_name, SUM(amount) as total, COUNT(*) as orders FROM sales WHERE date = CURRENT_DATE GROUP BY product_name ORDER BY total DESC`.
> 3. Dùng Python vẽ biểu đồ Bar Chart Top 10 sản phẩm bán chạy nhất hôm nay.
> 4. Lưu biểu đồ `DoanhThu_HomNay.png`.
> 5. Gửi biểu đồ qua Slack channel #sales kèm caption: "📊 Top 10 sản phẩm hôm nay (cập nhật lúc [giờ])."

**Kết quả kỳ vọng:**
> *"Đã truy vấn bảng `sales` (1.247 giao dịch hôm nay). Top 3: iPhone 16 Pro (89 đơn, 8.9 tỷ), Galaxy S25 (67 đơn, 5.4 tỷ), AirPods 4 (123 đơn, 615 triệu). Biểu đồ đã gửi qua #sales."*

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

## 4. Danh Sách MCP Server Phổ Biến Cho Doanh Nghiệp Việt

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

## 5. Quy Trình Tích Hợp MCP Cho SME (Step-by-Step)

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

## 6. Troubleshooting MCP

| Sự Cố | Nguyên Nhân | Giải Pháp |
| :--- | :--- | :--- |
| `MCP Server not found` | Chưa cài Node.js hoặc npx | Chạy: `brew install node` (macOS) hoặc xem [Phụ lục](phu-luc-cai-dat-moi-truong.md) |
| `Authentication failed` | API Key/Token hết hạn hoặc sai | Kiểm tra lại Key trong file `settings.json`. Tạo Key mới nếu cần. |
| `Permission denied` khi đọc Sheet | Chưa share Sheet cho Service Account | Share Google Sheet cho email Service Account với quyền Viewer/Editor. |
| `Connection refused` khi kết nối DB | Database chưa cho phép kết nối từ bên ngoài | Thêm IP máy vào whitelist DB. Kiểm tra firewall. |
| MCP Server chạy chậm | Server MCP bị timeout do dữ liệu quá lớn | Giới hạn query: thêm `LIMIT 1000` vào SQL. Chia nhỏ request. |

---

## 📚 Tài Liệu Tham Khảo

- [Model Context Protocol — Tài liệu chính thức](https://modelcontextprotocol.io/)
- [Danh sách MCP Servers có sẵn](https://github.com/modelcontextprotocol/servers)
- [Hướng dẫn tạo MCP Server tùy chỉnh](https://modelcontextprotocol.io/docs/concepts/servers)
- [Chương 0 — Giới thiệu Antigravity](00-gioi-thieu-antigravity.md)
- [Chương 7 — Skills & Workflows](07-skills-va-workflows.md)
- [Phụ lục — Cài đặt môi trường](phu-luc-cai-dat-moi-truong.md)
