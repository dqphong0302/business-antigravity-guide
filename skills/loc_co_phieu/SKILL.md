---
name: Lọc Cổ Phiếu VN30 & Dự Đoán Điểm Mua (VN30 Scouter)
description: Kết nối SSI iBoard lấy dữ liệu thời gian thực rổ VN30. Kết hợp Phân tích Kỹ thuật (TA) và Cào tin tức thị trường (News Sentiment) để dự đoán ngưỡng vào tiền an toàn nhất.
---

# Skill: Giám Sát VN30 & Bắt Điểm Mua Bằng TA (SSI iBoard)

## Bối Cảnh Sử Dụng

Skill này được thiết kế dựa trên triết lý "Cắt Lỗ Cảm Tính". Bằng cách tập trung vào rổ Blue-chips (VN30) và dùng Nguồn dữ liệu từ bảng điện uy tín **SSI iBoard**, skill này kết hợp tín hiệu Biểu đồ kỹ thuật (TA) và Tin tức vĩ mô để chỉ ra vùng giá mua an toàn nhất mà Sếp cần đợi.

## Nguyên Liệu Đầu Vào

- **Nguồn cấp:** API/Scraping trực tiếp từ [SSI iBoard](https://iboard.ssi.com.vn/).
- **Phạm vi giám sát:** 30 Cổ phiếu vốn hóa lớn VN30 (HPG, FPT, VCB, CTG...).
- **Chỉ báo phân tích chính:** Kỹ thuật (RSI, MACD, MA20/50, Vùng hỗ trợ/kháng cự) + Cảm nghĩ thị trường (Tin tức CafeF/Vietstock lưu lượng 24h).

## Quy Trình Thực Hiện

### Bước 1: Bắt Mạch SSI iBoard (Data Extraction)

- Sử dụng Python/Puppeteer kết hợp API hoặc Data stream từ bảng giá `SSI iBoard`.
- Kéo ngay Dữ liệu Lịch sử Giá (OHLCV) và lệnh khớp Buy/Sell chủ động của 30 mã VN30.

### Bước 2: Đo Đạc Biểu Đồ - Phân Tích Kỹ Thuật (TA)

```python
# Pseudo-code logic xác định Vùng Mua
df_vn30 = lay_du_lieu_ssi_iboard('VN30')

# Sàng lọc điểm mua kỹ thuật
tin_hieu_mua = df_vn30[
    (df_vn30['RSI'] <= 35) & # Đã bán tháo quá đà
    (df_vn30['Gia_Hien_Tai'] <= df_vn30['Vung_Ho_Tro_Manh_MA50']) &
    (df_vn30['MACD_Histogram'] > df_vn30['MACD_Histogram'].shift(1)) # Đà giảm đã chững lại
]
```

### Bước 3: Đối Chiếu Cảm Tính (News Sentiment)

- Browser Agent được lệnh search nhanh luồng tin trong 24h về các Doanh nghiệp Vừa lọt lưới Kỹ thuật.
- Nếu cổ phiếu FPT thủng MA50 CHỈ VÌ thị trường chung sập (Panic) -> Báo Tín hiệu **BẮT ĐÁY MẠNH**.
- Nếu FPT thủng MA50 VÌ tin tức "Bắt Giám Đốc" -> Báo Tín hiệu **HỦY BỎ/BỎ QUA LƯỚI KHỚP LỆNH**.

### Bước 4: Chống Án - Cấp Lệnh Khuyến Nghị (Entry Point)

- Cung cấp "Ngưỡng Vào Tiền Dự Đoán": Vd *(Cổ TCB: Vùng Mua 22.5 - 23.0; Cắt Lỗ: 21.0; Chốt Lời: 26.5)*.
- Xuất thành Bảng Phân Tích Khuyến Nghị Markdown.

## Ví Dụ Prompt Gọi Skill

```text
"Kẹp nguồn từ bảng giá SSI iBoard nhé. 
Hãy quét 30 mã VN30 hiện tại và chạy các indicator cơ bản: RSI, MACD, MA20, MA50. 
Phát hiện giúp tôi 2 mã nào đang có RSI phân kỳ dương hoặc đang tiệm cận vùng hỗ trợ cứng nhất lịch sử.
Sau đó cào nhanh tin tức thị trường xem có phốt nào ko.
Nếu ổn, hãy đề xuất cho tôi 1 mức NGƯỠNG VÀO TIỀN an toàn, điểm cắt lỗ và giải thích lý do bằng phân tích TA."
```
