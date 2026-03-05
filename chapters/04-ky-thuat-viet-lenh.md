# Chương 4: Kỹ Thuật Viết Lệnh (Prompt Engineering) — Masterclass Cho Doanh Nghiệp

> [!NOTE]
> Người mù công nghệ vẫn có thể điều khiển AI thành thạo, miễn là họ biết cách ra lệnh đúng công thức.

![Sơ đồ Framework Kỹ sư Prompt Nhập Môn](images/prompt_engineering_rtf_framework.png)

## 4.1. Sự Thật Về "Prompt Engineering" (Kỹ Thuật Kỹ Sư Lệnh)

Nhân viên của bạn thường than phiền: *"AI viết văn dở lắm"* hay *"Nó tính toán sai số hoài"*. Lỗi không nằm ở AI, lỗi nằm ở người ra lệnh (Prompter).

> [!IMPORTANT]
> **Tư duy lõi:** Prompt Engineering không phải là học code lập trình rắc rối. Nó đơn thuần là nghệ thuật giao tiếp cực kỳ **mạch lạc, không ngữ cảnh ngầm, và có đầy đủ tham số**.

---

## 4.2. Khung Công Thức R-T-F (Role - Task - Format)

Đây là khung xương sống vững chắc nhất, dễ hiểu nhất dành cho khối kinh tế, không chạm tới một dòng code nào. Bất cứ câu lệnh nào gửi cho Antigravity cũng phải chứa đủ 3 thành phần này.

### 🧩 Chữ R: Role (Khoác Áo Chuyên Gia)

- **Luật:** Đừng bao giờ để AI khởi động với tư cách "Một con Bot rỗng tuếch". Hãy ép nó nhập vai thành một chuyên gia 15 năm kinh nghiệm có độ "lõi đời".
- **Ví dụ Báo Kinh Doanh:** *"Hành động như một Giám đốc Tài chính (CFO) nghiêm khắc có 15 năm kinh nghiệm soát lỗi Báo cáo ngân lưu tại Big 4."*
- **Tại sao?** Khi được nạp Role, AI sẽ tự giới hạn kho từ vựng và tư duy xuống góc nhìn của Chuyên gia Tài chính, dẹp bỏ các ngôn từ hoa mỹ xáo rỗng của dân Marketing.

### 🧩 Chữ T: Task (Giao Việc Trực Diện & Đặt Ranh Giới)

- **Luật:** Giao đúng 1 việc, cắt nghĩa rõ ràng những gì KHÔNG ĐƯỢC LÀM.
- **Ví dụ Kế Toán:** *"Nhiệm vụ của bạn là soi chéo File A (Sao kê ngân hàng) và File B (Hóa đơn nội bộ). Nhiệm vụ số 1: Tìm ra các khoản tiền trên File B nhưng hoàn toàn biến mất trên File A. TUYỆT ĐỐI KHÔNG SANG CHẾ THÊM SỐ LIỆU."*

### 🧩 Chữ F: Format (Đổ Khuôn Định Dạng)

- **Luật:** AI có xu hướng thích "Nói dông dài để tỏ ra có ích". Phải ép nó trả về kết quả dưới dạng Bảng Biểu (Table), Danh sách Bullet, hay Code Block để bạn còn Copy-Paste ra Excel.
- **Ví dụ HR:** *"Chỉ trả kết quả dưới dạng Markdown Table gồm 3 Cột: [Tên Ứng Viên], [Điểm Phù Hợp %], và [Câu Hỏi Phỏng Vấn Sắc Bén Nhất]. Cấm vòng vo."*

---

## 4.3. Khung Nâng Cao: C.R.E.A.T.E Framework

Khi muốn Antigravity viết các bản Kế hoạch Kinh doanh, Báo giá hoặc Tài liệu Đào tạo phức tạp dài 5 trang, RTF là chưa đủ. Hãy chuyển sang Khung C.R.E.A.T.E.

1. **C (Context - Ngữ cảnh):** Bơm máu cho AI. *"Công ty tôi bán máy lọc nước cho nhà xưởng. Giá cao gấp đôi thị trường mạnh nhưng lõi lọc bền gấp 3."*
2. **R (Request - Yêu cầu):** Giao việc cụ thể. *"Hãy viết 1 thư chào mời Giám đốc sản xuất của Nhà máy VinaMilk mua thử."*
3. **E (Explanation - Giải thích rõ đối tượng):** Phác họa người đọc. *"Giám đốc VinaMilk rất bận, chỉ có 10 giây lướt Email, và cực kỳ ghét văn phong lủng củng sale."*
4. **A (Action - Hành động kỳ vọng):** Bạn muốn khách làm gì? *"Sau khi đọc thư, khách phải click vào link xem Báo Giá đính kèm."*
5. **T (Tone - Giọng điệu):** *"Văn phong chuyên nghiệp, tôn trọng lãnh đạo, đánh thẳng vào chỉ số tiết kiệm điện (ROI)."*
6. **E (Extra - Thông tin phụ):** Truyền thêm file kiến thức gốc. *"Đây là link PDF brochure của máy. Chỉ lấy thông tin trong này."*

---

> [!TIP]
> **Tư duy của Khí tài Agent (Chain-of-Thought):** Bắt AI phải "Nghĩ Lớn Tiếng" từng bước một. Điều này giúp loại bỏ hoàn toàn lỗi ảo giác (Hallucination) trong các bài toán phức tạp.

*Sudo Prompt Áp dụng Chuỗi Tư Duy:*

```text
Tôi cung cấp cho bạn Báo cáo Doanh thu Q3.
Đừng vội đưa ra kết luận. Hãy suy luận TỪNG BƯỚC MỘT như sau:
- Bước 1: Tính toán % sụt giảm doanh thu của mảng "Bán lẻ online" so với Q2. In ra con số phân tích ngắn.
- Bước 2: Tìm trong file báo cáo chi phí xem mảng Marketing cho "Bán lẻ online" có bị cắt giảm tương ứng không. In ra nguyên nhân.
- Bước 3: Đưa ra nhận xét Mối quan hệ giữa Chi phí/Doanh thu.
- Bước 4: Cuối cùng, mới đưa ra kết luận có nên giải tán mảng Bán lẻ online hay không.
```

Bằng cách bắt AI phải viết ra các bước trung gian 1, 2, 3... bạn đang ép bộ não LLM chạy qua các chốt kiểm duyệt Logic cục bộ (Self-Verification), tránh hoàn toàn lỗi Halucination (Bịa số liệu).

---

### [Checklist Thực Hành Cho Trưởng Phòng]

- [ ] Mở buổi họp thứ hai đầu tuần, bắt toàn bộ nhân sự Marketing luyện tập viết lệnh chia ba cấu trúc RTF. Cấm gửi lệnh 1 dòng.
- [ ] Bổ sung Câu lệnh (System Prompt) vào đuôi các quy trình SOP của Doanh nghiệp.
- [ ] Soạn sẵn Bộ Sudo Prompt chuỗi tư duy (Chain-of-Thought) cho Kế toán đối soát chứng từ cuối tháng.

---

## 4.5. Case Study Thực Chiến: Team Marketing & Nỗi Đau "Viết Lệnh Nhờn Bot"

**Bối cảnh:** Một SME bán ghế Massage chạy chiến dịch Facebook Ads. Nhân sự Content Mới vào gõ lệnh cho tài khoản ChatGPT Plus của Công ty: *"Viết 1 bài QC bán ghế massage giảm giá 20%"*.
**Kết quả:** Trí tuệ AI trị giá hàng tỷ đô la trả về một đoạn văn... buồn ngủ, sặc mùi Ráp-bốt (Robot) với những Emoji 🚀 tràn lan. "Giới thiệu siêu phẩm ghế massage... giúp bạn thư giãn... Mua ngay!". Lỗ nặng tiền Ads.

**Cách Thức Xử Lý Bằng Antigravity (System Design of the Prompt)**
Trưởng phòng Marketing quyết định Đóng gói (Encapsulate) tư duy C.R.E.A.T.E thành một file Kỹ năng (Skill) cứng trong thư mục Antigravity. Từ nay, nhân viên không được chat chay nữa, chỉ việc gõ `Slash Command` và điền biến số.

**Cấu trúc File Mẫu: `skills/viet_bai_fb_ads/SKILL.md`**

```yaml
---
name: "Viết Bài C.R.E.A.T.E Facebook Ads"
description: "Ép AI viết bài QC tuân thủ điểm đau tâm lý theo công thức C.R.E.A.T.E"
version: 1.0.0
category: "Marketing"
---
# 🎯 Lệnh: `/viet-ads`

## 1. System Role (Vai trò Hệ thống)
Bạn là một "Mãng tướng Hắc Sắc Marketing" chuyên viết Facebook Ads thực dụng. Bạn khinh bỉ những văn phong câu view rẻ tiền và rập khuôn. Giọng văn của bạn: Đanh thép, Xoáy sâu nỗi đau (Pain points), Ngôn từ đời thường không bóng bẩy.

## 2. Context & Request (Ngữ cảnh & Yêu cầu)
Sản phẩm: Ghế Massage M12.
Nỗi đau Khách Hàng: Đau mỏi vai gáy kinh niên do làm văn phòng, hay mua thuốc giảm đau nhưng không khỏi. Mức giá ghế hơi cao nên họ tiếc tiền.
Yêu cầu: Viết 1 bài Facebook Ads (Tối đa 300 chữ).

## 3. Action & Tone (Hành động & Giọng điệu)
Hành động: Ép người đọc phải chốt Inbox ngay hôm nay vì ưu đãi Giảm 20% chỉ có 5 slot.
Giọng điệu: Đồng cảm, nhưng thúc giục quyết liệt.

## 4. Format & Verification (Định dạng & Xác Thực)
Không dùng quá 3 Emoji. Dùng cấu trúc: Tiêu đề giật gân (IN HOA) -> Nỗi đau -> Giải pháp (Ghế M12) -> Call-to-action.
```

### 👣 Quy trình 4 bước đóng gói Kỹ năng (Skill) cho phòng Marketing

**Bước 1: Khai phá Thư mục Skill**

- 📁 Mở Antigravity, tìm đến thư mục `D:\antigravity\skills\`.
- 📁 Tạo thư mục mới: `viet_bai_fb_ads`.

**Bước 2: Đúc khuôn trí tuệ (SKILL.md)**

- 📝 Tạo file `SKILL.md` và dán khung C.R.E.A.T.E (Vai trò, Ngữ cảnh, Yêu cầu...) vào trong. Nhấn Lưu.

**Bước 3: Triệu hồi trợ lý (Slash Command)**

- 💭 Quay lại Antigravity Chat, gõ lệnh tắt:

  ```text
  /run-skill viet_bai_fb_ads Sản_phẩm="Ghế Massage", Khuyến_mãi="20%"
  ```

**Bước 4: Duyệt & Tối ưu**

- 🚀 AI sẽ tự động đọc file Skill, gò bài viết vào đúng Tone & Mood sếp quy định. Sếp chỉ việc gật đầu duyệt bài.
