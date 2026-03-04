# Dự Án Mẫu: Đối Soát Dòng Tiền COD Tự Động

## Mục đích

Đây là dự án mẫu **hoạt động được thực tế** để anh/chị Kế toán trải nghiệm sức mạnh của Antigravity. Dự án bao gồm:

- **Source code Python** chạy được ngay
- **Data mẫu** (2 file CSV giả lập)
- **Case Study phân tích chi tiết** `/case-study.md`
- **Skill hỗ trợ** sẵn sàng trong `/skills/`

## Cách sử dụng

### Bước 1: Mở Antigravity trong thư mục này

Mở Antigravity (hoặc IDE có tích hợp Antigravity), trỏ workspace vào thư mục `demo-project/`.

### Bước 2: Copy-Paste Prompt sau vào Antigravity

```
Hỡi Antigravity, hãy thực thi Skill đối soát ngân hàng cho tôi.

VỊ THẾ: Bạn là Kế toán trưởng kiểm toán nội bộ.
INPUT: Tại thư mục hiện tại, có 2 file:
- `data/noi_bo.csv` (Đơn hàng nội bộ từ KiotViet)
- `data/doi_tac.csv` (Sao kê từ đối tác vận chuyển)

TIẾN TRÌNH:
[1] Đọc 2 file. Chuẩn hóa cột SĐT (xóa khoảng trắng, chuyển +84 thành 0).
[2] Dùng Pandas merge (outer). Tìm: Đơn thất thoát, Đơn ảo, Đơn chênh lệch tiền.
[3] Xuất file `ket_qua_doi_soat.xlsx` gồm 3 sheets. Tô đỏ các ô tiền chênh lệch.

RÀNG BUỘC: Chỉ đọc file gốc. Cấm sửa. Cấm đoán mò số liệu.
```

### Bước 3: Xem kết quả

AI sẽ tự động viết code Python, chạy và xuất file `ket_qua_doi_soat.xlsx` với 3 sheet báo cáo.

## Cấu trúc thư mục

```
demo-project/
├── README.md              ← Bạn đang đọc file này
├── case-study.md          ← Phân tích Case Study chi tiết
├── data/
│   ├── noi_bo.csv         ← Data mẫu: Đơn hàng nội bộ
│   └── doi_tac.csv        ← Data mẫu: Sao kê đối tác
└── skills/
    └── doi_soat_ngan_hang/
        └── SKILL.md       ← Skill hỗ trợ đối soát
```
