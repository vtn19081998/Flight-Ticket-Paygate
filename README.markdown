# Flight Ticket Paygate

## Giới thiệu
Dự án này là một giao diện cổng thanh toán trực tuyến được thiết kế để cung cấp các phương thức thanh toán an toàn và tiện lợi cho người dùng. Giao diện hỗ trợ nhiều phương thức thanh toán như chuyển khoản ngân hàng, thẻ ATM, thẻ tín dụng qua VNPAY và OnePay, đồng thời tích hợp tính năng tạo mã VietQR để thanh toán nhanh.

## Ảnh giao diện
![Giao diện cổng thanh toán trực tuyến](./data/screenshot.jpg)

## Tính năng
- **Lựa chọn phương thức thanh toán**:
  - Chuyển khoản ngân hàng (miễn phí giao dịch).
  - Thẻ ATM/Tài khoản ngân hàng (phí 1,2%).
  - Thẻ ATM nội địa qua VNPAY (phí 1%).
  - Thẻ tín dụng qua OnePay (phí 3,4%).
  - Thẻ tín dụng qua VNPAY (phí 2,5%).
- **Tạo mã VietQR**: Tự động tạo mã QR dựa trên thông tin tài khoản ngân hàng, số tài khoản và tên tài khoản.
- **Sao chép thông tin thanh toán**: Cho phép sao chép nội dung thanh toán (tên tài khoản, số tiền, nội dung, ngân hàng, số tài khoản) vào clipboard.
- **Chụp ảnh màn hình**: Chụp và sao chép ảnh khu vực thanh toán (bao gồm mã VietQR) vào clipboard hoặc tải xuống dưới dạng tệp PNG.
- **Lưu trữ cục bộ**: Lưu thông tin nhập vào (localStorage) để khôi phục khi tải lại trang.
- **Hỗ trợ chuẩn hóa dữ liệu**: Loại bỏ dấu tiếng Việt và chuẩn hóa dữ liệu đầu vào (tên tài khoản, nội dung).
- **Giao diện thân thiện**: Thiết kế responsive, hỗ trợ accessibility (ARIA labels, keyboard navigation).

## Công nghệ sử dụng
- **HTML5**: Cấu trúc giao diện.
- **CSS3**: Tùy chỉnh giao diện (tệp `styles.css`).
- **JavaScript**: Xử lý logic, tương tác người dùng và tích hợp API VietQR.
- **html2canvas**: Chụp ảnh màn hình khu vực thanh toán.
- **LocalStorage**: Lưu trữ thông tin tạm thời trên trình duyệt.
- **VietQR API**: Tạo mã QR thanh toán.

## Cài đặt
1. **Tải xuống dự án**:
   - Clone repository hoặc tải mã nguồn về máy.
2. **Cấu trúc thư mục**:
   ```
   /data
     ├── styles.css           # Tệp CSS cho giao diện
     ├── favicon.ico          # Icon trang web
     ├── logovnpayqr.png      # Logo VNPAYQR
     ├── logovietqr.png       # Logo VietQR
     ├── html2canvas.min.js   # Thư viện html2canvas
     ├── screenshot.jpg       # Ảnh giao diện
   index.html                 # Tệp HTML chính
   README.md                  # Tệp hướng dẫn này
   ```
3. **Chạy dự án**:
   - Mở tệp `index.html` trong trình duyệt (khuyến nghị Chrome, Firefox).
   - Đảm bảo kết nối internet để tải mã VietQR và thư viện html2canvas.

## Sử dụng
1. **Nhập thông tin thanh toán**:
   - Điền **Tên tài khoản**, **Số tiền**, **Nội dung**, **Ngân hàng**, và **Số tài khoản**.
   - Thông tin sẽ được hiển thị trong khu vực thanh toán và tự động lưu vào localStorage.
2. **Tạo mã VietQR**:
   - Sau khi nhập đầy đủ thông tin hợp lệ, mã VietQR sẽ tự động được tạo và hiển thị.
3. **Sao chép nội dung**:
   - Nhấn nút "Sao chép nội dung" để sao chép thông tin thanh toán vào clipboard.
   - Nhấn "Copy" bên cạnh nội dung để sao chép riêng nội dung chuyển khoản.
4. **Chụp ảnh màn hình**:
   - Nhấn nút "Chụp ảnh màn hình" để sao chép ảnh khu vực thanh toán vào clipboard hoặc tải xuống dưới dạng PNG.

## Lưu ý
- **Yêu cầu kết nối internet**: Cần kết nối để tải mã VietQR và thư viện html2canvas.
- **Hỗ trợ ngân hàng**: Hệ thống hỗ trợ hơn 25 ngân hàng phổ biến tại Việt Nam (xem danh sách trong `index.html`).
- **Chuẩn hóa dữ liệu**:
  - Tên tài khoản được chuyển thành chữ in hoa và loại bỏ dấu tiếng Việt.
  - Số tài khoản chỉ chấp nhận chữ số.
  - Nội dung thanh toán được tạo ngẫu nhiên khi nhập số tiền (bao gồm ký tự 0 và O).
- **Bảo mật**: Không lưu trữ thông tin nhạy cảm trên server, chỉ sử dụng localStorage trên trình duyệt người dùng.

## Tùy chỉnh
- **Thay đổi giao diện**: Chỉnh sửa tệp `styles.css` để tùy chỉnh màu sắc, bố cục.
- **Thêm ngân hàng**: Cập nhật danh sách ngân hàng và mã BIN trong biến `bankBins` trong phần `<script>` của `index.html`.
- **Tích hợp thêm API**: Có thể tích hợp thêm API thanh toán khác (VNPAY, OnePay) để xử lý giao dịch thực tế.

## Giải quyết sự cố
- **Mã VietQR không hiển thị**:
  - Kiểm tra kết nối internet.
  - Đảm bảo thông tin nhập (tên tài khoản, số tài khoản, ngân hàng) hợp lệ.
  - Kiểm tra console trình duyệt để xem lỗi chi tiết.
- **Chụp ảnh màn hình không hoạt động**:
  - Đảm bảo tệp `html2canvas.min.js` được tải đúng.
  - Kiểm tra quyền clipboard trên trình duyệt.
- **Dữ liệu không lưu**:
  - Đảm bảo trình duyệt hỗ trợ localStorage và không ở chế độ riêng tư (private mode).

## Đóng góp
- Nếu bạn muốn đóng góp, vui lòng fork repository, tạo branch mới, và gửi pull request.
- Báo lỗi hoặc đề xuất tính năng qua mục Issues.

## Giấy phép
Dự án này được phát hành dưới [Giấy phép MIT](LICENSE). Bạn có thể sử dụng, chỉnh sửa và phân phối mã nguồn theo các điều khoản của giấy phép.