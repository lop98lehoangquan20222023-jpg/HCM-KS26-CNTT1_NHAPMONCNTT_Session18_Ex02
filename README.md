# Phần 1. Phân tích (Cache vs Cookies)
1. Cache:

- Dung lượng: Lớn (MB/GB).

- Lưu trữ: Ảnh, file CSS, JavaScript để tải trang nhanh hơn.

- Đánh đổi: Tốc độ nhanh nhưng dễ bị lưu lại giao diện cũ.

2.  Cookies:

- Dung lượng: Rất nhỏ (~4 KB).

- Lưu trữ: Mẩu tin nhận diện (Token) giúp hệ thống nhớ trạng thái đăng nhập.

- Đánh đổi: Gọn nhẹ, an toàn nhưng không đủ chỗ chứa các dữ liệu lớn như giỏ hàng phức tạp.

# Phần 2. Triển khai (Cấu trúc Cookie duy trì phiên)
Để shipper không bị mất giỏ hàng hay bắt đăng nhập lại khi đóng trình duyệt, Server sẽ cấp phát Persistent Cookie với cấu trúc:

```HTTP
Set-Cookie: session_id=<token_ngẫu_nhiên>; Max-Age=604800; HttpOnly; Secure
```
Max-Age=604800: Giữ phiên làm việc trong 7 ngày, đóng trình duyệt cũng không bị mất đăng nhập.

HttpOnly: Ngăn mã JavaScript của bên thứ ba đọc trộm cookie

Secure: Bắt buộc truyền qua mạng HTTPS an toàn.

Phần 3. Kiểm thử (Xử lý giao diện cũ)
Nếu hệ thống đã đổi màu sắc nhưng trình duyệt vẫn hiện giao diện cũ do Cache:

Cách nhanh nhất: Nhấn tổ hợp phím Ctrl + Shift + R (Hard Reload) để ép trình duyệt xóa bộ nhớ đệm và tải lại bản mới hoàn toàn.