# Phần 1. Phân tích (Box Model)
Nguyên nhân: Khung bị lỗi do dùng margin: -34px (margin âm) kết hợp width: 118% và z-index: 99999, khiến nó phình to và đè lên khung bên cạnh.

# Phần 2. Triển khai (Sửa trên DevTools)
Nhập các thông số mới tại tab Styles để tách khung:

```CSS
element.style {
    margin: 0px;
    width: 100%;
    padding: 15px;
    z-index: 1;
   }
````
Phần 3. Kiểm thử (Khi sửa Margin nhưng không dịch chuyển)
Kiểm tra position: Nếu để position: static, margin âm sẽ không có tác dụng .

Kiểm tra ghi đè: Xem dòng CSS có bị gạch ngang không (do bị đoạn code khác có !important ghi đè).