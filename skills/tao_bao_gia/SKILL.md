---
name: Tạo Báo Giá Tự Động (Auto Quotation Generator)
description: Đọc danh sách sản phẩm và bảng chiết khấu, tự động tạo file Báo giá PDF/Excel chuyên nghiệp gửi khách hàng.
---

# Skill: Tạo Báo Giá Tự Động

## Bối Cảnh Sử Dụng

Skill này kích hoạt khi Sales/Kinh doanh cần tạo báo giá cho khách hàng dựa trên danh mục sản phẩm và chính sách chiết khấu.

## Quy Trình Thực Hiện

1. Đọc file Danh Mục Sản Phẩm (`san_pham.xlsx`) lấy Tên, Đơn giá gốc, Đơn vị tính.
2. Đọc file Chính Sách Chiết Khấu (`chiet_khau.xlsx`) lấy mức giảm theo số lượng/đối tác.
3. Nhận yêu cầu từ người dùng: Tên khách hàng, Danh sách SP cần báo giá, Số lượng.
4. Tính Đơn giá sau chiết khấu, Thành tiền, Tổng cộng, Thuế VAT 8%.
5. Xuất file Excel đẹp với Header công ty, Logo placeholder, và bảng chi tiết.
6. Ghi rõ: Hiệu lực báo giá 15 ngày, Điều kiện thanh toán.

## Lưu Ý

- Luôn đính kèm dòng "Giá chưa bao gồm VAT" hoặc "Giá đã bao gồm VAT" tùy chính sách.
