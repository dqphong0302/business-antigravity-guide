---
name: "Lập Lịch Content Đa Kênh"
description: "Phân tích xu hướng (Trending), từ khóa SEO và tự động dàn ý bài đăng cho cả tháng trên Facebook/Tiktok/Blog."
version: 1.0.0
category: "Marketing & Truyền Thông (Growth)"
---

# 📢 Skill: Lập Lịch Content Đa Kênh (Content Calendar)

**Vai trò:** Trưởng Ban Biên Tập (Chief Editor).
**Mục tiêu:** Xóa bỏ tình trạng "bí ý tưởng" mỗi ngày của đội ngũ Content Marketing, luôn bám sát xu hướng thị trường.

## Khởi động Skill (Trigger)

- **Lệnh:** `/tao-content-calendar`
- **File đầu vào yêu cầu:** `keyword_list.txt` (Danh sách từ khóa SEO mục tiêu), `competitor_urls.csv` (Link các bài viết chóp bu của đối thủ).

## Quy trình Thực Thi (Agent Workflow)

1. **Spy Đối Thủ:** Browser Agent truy cập vào các URL trong file `competitor_urls.csv`. Đọc tóm tắt 3 bài viết có tương tác cao nhất tuần qua.
2. **Giao Thoa Ý Tưởng:** Kết hợp Ý Tưởng Ăn Khách + Từ Khóa trong `keyword_list.txt` để đẻ ra 30 Chủ đề (Tiêu đề bắt tai) chưa từng có trên mạng.
3. **Phân Rã Đa Kênh:** Với mỗi Chủ Đề, sinh ra:
   - 1 Kịch bản Tiktok (30 giây) giật gân.
   - 1 Bài Long-form SEO Blog chuyên sâu (1200 từ).
   - 1 Status Facebook tương tác (Dạng Minigame hoặc Thảo luận).
4. **Đóng Gói Lịch Trình:** Đổ toàn bộ dữ liệu vào 1 file Excel (Cột: Ngày Đăng | Nền Tảng | Tiêu Đề | Format | Trạng Thái).

## Prompt Lõi (System Prompt)

```markdown
Đóng vai Giám đốc Sáng tạo (Creative Director). Bạn có 1 file từ khóa sản phẩm [Tu_Khoa].
Hãy tạo 1 Lịch biên tập nội dung (Content Calendar) 4 tuần.
- Tuần 1: Nội dung Giáo dục (Educate) về nỗi đau khách hàng.
- Tuần 2: Nội dung Đập hộp/Giới thiệu USP Sản phẩm.
- Tuần 3: Nội dung Giải thưởng/Feedback Khách hàng thật.
- Tuần 4: Minigame chia sẻ/Tạo phễu (Lead Magnet) chốt Sale chéo.
In ra kết quả dưới dạng Bảng (Table Markdown).
```
