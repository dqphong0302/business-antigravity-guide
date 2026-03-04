---
name: doi-soat-ngan-hang
description: Đối soát tự động giữa file nội bộ (KiotViet/Misa) và sao kê ngân hàng/đối tác vận chuyển. Phát hiện đơn thất thoát, đơn ảo và chênh lệch tiền.
---

# Skill: Đối Soát Ngân Hàng / Đối Tác Vận Chuyển

## Khi nào dùng Skill này?

- Cuối tháng đối soát sao kê ngân hàng vs file bán hàng
- Đối soát COD (Thu hộ) với đối tác vận chuyển (GHTK, Viettel Post, GHN...)
- So khớp 2 bảng dữ liệu bất kỳ có cột chìa khóa chung

## Yêu cầu đầu vào

1. **File A** (Nội bộ): Excel/CSV từ hệ thống bán hàng (KiotViet, Misa, Sapo...)
2. **File B** (Đối tác): Excel/CSV sao kê từ ngân hàng hoặc đối tác vận chuyển
3. **Cột chìa khóa**: Mã vận đơn, Mã giao dịch, hoặc SĐT khách hàng

## Quy trình thực thi (3 Agent)

### Agent 1: Data Cleaner (Thợ Dọn Dẹp)

```
- Đọc cả 2 file bằng Pandas
- Chuẩn hóa cột chìa khóa: Trim khoảng trắng, Uppercase, chuyển +84 → 0
- Chuẩn hóa cột tiền: Xóa dấu phẩy, ký tự "VNĐ", ép kiểu Float
- Nếu file dùng encoding khác UTF-8, thử cp1252 hoặc utf-8-sig
```

### Agent 2: Comparator (Trọng Tài Phán Xử)

```
- Dùng pd.merge(how='outer') trên cột chìa khóa
- Phân loại 3 nhóm:
  1. THAT_THOAT: Có ở File A, không có ở File B
  2. DON_AO: Có ở File B, không có ở File A
  3. CHENH_LECH: Có ở cả 2 nhưng số tiền khác nhau (abs(A-B) > 0)
```

### Agent 3: Reporter (Thợ Báo Cáo)

```
- Xuất file Excel (.xlsx) gồm 3 sheets tương ứng 3 nhóm
- Sheet CHENH_LECH: Tô nền đỏ cho ô tiền bị lệch (dùng openpyxl)
- In tổng kết: Số đơn mỗi nhóm + Tổng tiền bị ảnh hưởng
```

## Prompt mẫu (Copy-Paste)

```
SUDO PROMPT: ĐỐI SOÁT DÒNG TIỀN THÁNG [X]

VỊ THẾ: Kế toán trưởng kiểm toán nội bộ.
INPUT: Tại `/[Thư_Mục]/`:
- File nội bộ: `[tên_file_A].csv`
- File đối tác: `[tên_file_B].xlsx`
- Cột chìa khóa: [Mã Vận Đơn / SĐT]

TIẾN TRÌNH:
[1] Clean data: Trim, chuẩn hóa SĐT (+84→0), ép tiền về Float.
[2] Merge outer. Phân 3 nhóm: Thất thoát, Đơn ảo, Chênh lệch.
[3] Xuất `Doi_Soat_Thang_[X].xlsx` gồm 3 sheets. Tô đỏ ô lệch.

RÀNG BUỘC: Read-only file gốc. Cấm đoán mò. Nếu cột trống ghi NULL.
```

## Lỗi thường gặp

| Lỗi | Cách khắc phục |
|---|---|
| Merge ra toàn NULL | Kiểm tra tên cột chìa khóa giữa 2 file có giống nhau không |
| SĐT không khớp | Thêm bước chuẩn hóa: xóa khoảng trắng, chuyển +84 → 0 |
| UnicodeDecodeError | Thêm `encoding='utf-8-sig'` hoặc `encoding='cp1252'` |
| File quá lớn (>50MB) | Dùng `chunksize=5000` khi đọc, hoặc chuyển sang Gemini Pro |
