# Phụ Lục Đặc Biệt: Hướng Dẫn "Tay Ngang" Cài Đặt Môi Trường Tự Động Hóa (Python & Node.js)

*(Cẩm nang dành cho CEO và Nhân sự không chuyên IT)*

---

## 1. Mở Đầu: Tại Sao Máy Tính Của Bạn Từ Chối "Robot"?

Trong các chương trước, bạn đã thấy Antigravity làm đủ trò ma thuật: Đọc file Excel, vẽ biểu đồ, cào dữ liệu từ Website.
Nhưng để Antigravity làm được những điều đó, MÁY TÍNH CỦA BẠN (Windows hoặc MacOS) cần phải có "Đất diễn". Máy tính bình thường chỉ biết mở Word, Excel, Chrome. Nó không hiểu các dòng lệnh "Sudo Code" hoặc "Script" mà Antigravity đẻ ra.

Để AI chạy được Code tự động hóa, bạn cần cài đặt 2 "Vùng Đất" lên máy tính:

1. **Python:** Trái tim của Phân tích Dữ liệu, Excel, Đọc PDF và Khoa học Máy tính.
2. **Node.js:** Động cơ của Web, Cào dữ liệu Website (Scraping), Webhook và Tự động hóa trình duyệt.

Đừng hoảng sợ! Việc cài đặt này chỉ diễn ra **1 LẦN DUY NHẤT** trong đời cái máy tính đó. Và thao tác của nó giống hệt như việc bạn tải và bấm "Next -> Next -> Finish" cài Zalo thôi.

Dưới đây là Hướng dẫn Cầm tay chỉ việc 100%.

---

## 2. Cài Đặt Không Gian Python (Kẻ Hủy Diệt Dữ Liệu)

### Đối Với Người Dùng WINDOWS

**Bước 1: Tải bộ cài đặt**

- Mở trình duyệt, truy cập trang chủ: `https://python.org/downloads/`
- Bấm vào nút màu vàng to đùng: **"Download Python 3.xxx"** (Phiên bản mới nhất).

**Bước 2: CÀI ĐẶT (GHI NHỚ NÚT CHECKBOX SINH TỬ)**

- Mở file `.exe` vừa tải về lên.
- 🚨 **CẢNH BÁO CAO ĐỘ:** Ở màn hình Cài đặt Đầu tiên CỰC KỲ QUAN TRỌNG. Bạn NHÌN XUỐNG DƯỚI CÙNG sẽ thấy một ô vuông nhỏ ghi chữ:
  `[✓] Add Python 3.x to PATH` => **BẮT BUỘC PHẢI TÍCH (CHECK) VÀO Ô NÀY!** (Nếu quên tích, máy tính sẽ mù, AI sẽ không gọi được Python).
- Sau khi Tích vào ô đó, bấm chữ **"Install Now"** ở trên. Chờ thanh chạy đầy. Bấm Finish.

### Đối Với Người Dùng MAC (Apple/MacBook)

**Bước 1: Tải bộ cài**

- Tương tự, vào `https://python.org/downloads/mac-osx/` tải bản gốc `.pkg` cho MacOS. Hoặc cài tự động qua Homebrew.
- Bấm cài đặt "Tiếp tục" -> "Đồng ý" -> Cấp mật khẩu máy tính.
- MacOS tự động nhận diện Biến Môi trường nên Không cần lo vụ Add PATH như Windows.

---

## 3. Cài Đặt Động Cơ Node.js (Siêu Nhện Cào Dữ Liệu)

Sau khi có Python, máy bạn đã tính toán rất giỏi. Giờ cài thêm Hệ thần kinh Đa Liệu Web.

**Bước 1: Tải bộ cài đặt từ Trang Chủ**

- Vào Web: `https://nodejs.org/`
- Màn hình hiện ra 2 nút màu xanh lá cây. HÃY BẤM VÀO NÚT CÓ CHỮ: **"LTS (Recommended For Most Users)"** (Bản ổn định nhất). Tuyệt đối Đừng tải bản "Current" vì dễ dính Lỗi Mới.

**Bước 2: Cài Đặt Node.js**

- **Windows:** Mở file `.msi` vừa tải. Cứ bấm `Next` liên tục. Mọi thông số Default (Mặc định) đều đã tối ưu. (Phần mềm này Tự động Thêm PATH cho Windows nên sếp không cần thao tác tay). Bấm Install.
- **Mac:** Mở file `.pkg` và cài đặt bình thường qua dòng lệnh cài đặt Mac App.

---

## 4. Kiểm Chuẩn Sức Mạnh (Lễ Đăng Quang Máy Tính)

Máy tính của Sếp đã lột xác! Làm sao để biết 2 Động cơ này đã Nổ Máy thành công trong Hệ điều hành? Sếp chỉ cần dùng Antigravity hoặc Mở bảng Đen Terminal.

**Hành động Thích Đáng Nhất:**
Mở Chatbox của Antigravity, Ra lệnh bằng giọng điệu Vua Chúa:
> *"Em Antigravity, Mở hộ anh cái Terminal. Gõ lệnh kiểm tra `python --version` và `node --version` xem máy tính anh đã Có đủ Hai Nền tảng em yêu cầu chưa nhé?"*

Nếu Màn hình Antigravity báo về:

- `Python 3.12.x` (Hoặc lớn hơn).
- `Current Node v20.x` (Hoặc lớn hơn).

**=> CHÚC MỪNG SẾP!**
Cỗ Máy Laptop Cổ Lỗ Sĩ của Sếp giờ đây đã trở thành Trạm Rẽ Sóng Máy Chủ Không Gian Số. Sếp có thể Kéo thả Hàng Vạn File Excel, hay Bắt nó Dựng Cổng Nhận Webhook Từ Bây giờ, Nó Sẽ Nuốt Trọn Không Còn Nghẹn Cổ Nữa!

---
*(Phụ Lục này được thiết kế Đính Kèm Cú Cuốn Sách Khép Giờ Cuối Cùng. Xin giữ kỹ như Chìa khóa vào phòng Máy Chủ).*
