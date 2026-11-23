# Hướng dẫn sử dụng AdPlay

AdPlay giúp tải video/hình ảnh lên kho nội dung, ghép chúng thành playlist và phát playlist trên TV, tablet hoặc màn hình khác.

## 1. Khởi động ứng dụng

Trên máy đã cài Node.js:

- Windows: chạy `start.bat`.
- macOS: chạy `start.command` hoặc `./start.sh`.
- Linux: chạy `./start.sh`.

Lần đầu khởi động có thể mất vài phút để cài dependencies và build ứng dụng. Giữ cửa sổ terminal đang chạy mở trong suốt thời gian sử dụng.

## 2. Đăng nhập trang quản trị

Mở:

```text
http://localhost:3000/admin
```

Thông tin đăng nhập mặc định khi chạy lần đầu:

```text
Tên đăng nhập: admin
Mật khẩu: admin
```

Hãy đổi thông tin này trước khi cho người khác truy cập. Dừng ứng dụng, sửa `ADMIN_USERNAME` và `ADMIN_PASSWORD` trong `backend/.env`, sau đó khởi động lại.

## 3. Tải nội dung lên

1. Chọn **Kho Nội Dung**.
2. Nhấn ô **Tải Nội Dung Mới** và chọn file trên máy.
3. Chờ tiến trình tải lên hoàn tất. Video có thể tiếp tục được xử lý sau khi tải xong; hình ảnh thường sẵn sàng ngay.
4. Dùng nút xem trước trên thẻ nội dung để kiểm tra file.

Định dạng hỗ trợ:

- Video: MP4, WebM, OGG, MOV.
- Hình ảnh: JPG, PNG, GIF, WebP.

Kho nội dung có thể tìm theo tên và sắp xếp theo mới nhất, dung lượng, số playlist đang dùng hoặc tên file.

## 4. Tạo playlist cho một màn hình

Trong AdPlay, một cấu hình **Màn Hình** cũng là một playlist:

1. Chọn **Quản Lý Màn Hình** > **Tạo Mới**.
2. Nhập tên dễ nhận biết, ví dụ `Menu tầng 1`.
3. Chọn nội dung trong **Kho Nội Dung** để thêm vào playlist, hoặc kéo nội dung sang cột **Playlist Phát**.
4. Kéo thả các mục trong playlist để đổi thứ tự phát. Có thể bỏ một mục khỏi playlist bằng nút xóa cạnh mục đó.
5. Nhấn **Lưu**.

Mỗi playlist cần có tên riêng và ít nhất một nội dung. Có thể mở cấu hình để thay đổi tên, thêm/bỏ nội dung hoặc sắp xếp lại thứ tự. Sửa playlist đã lưu sẽ cập nhật nội dung trên player đang dùng playlist đó.

## 5. Mở player trên TV hoặc thiết bị khác

1. Kết nối thiết bị phát và máy chạy AdPlay vào cùng mạng Wi-Fi/LAN.
2. Trong trang quản trị, mở **Quản Lý Màn Hình** và tìm đúng màn hình.
3. Mở liên kết **Player mới** trên TV/tablet. Nếu trình duyệt quá cũ, thử liên kết **TV cũ**.
4. Nếu player hiện danh sách màn hình, chọn playlist cần phát.

Có thể lấy địa chỉ IP của máy chủ từ **Trạng Thái Hệ Thống** hoặc file `AdPlay Access.txt`. Trên thiết bị khác, dùng IP của máy chủ thay cho `localhost`, ví dụ:

```text
http://192.168.1.50:3000/player
```

Player được ghép với playlist khi mở liên kết có quyền truy cập lần đầu; token ghép nối được lưu trên thiết bị và thường được xóa khỏi thanh địa chỉ. Nếu thiết bị không hoạt động, mở lại liên kết ghép nối của playlist đó.

Video và hình ảnh trong playlist được phát luân phiên theo thứ tự đã sắp xếp. Một số TV yêu cầu chạm/bấm nút OK lần đầu để bật âm thanh hoặc chế độ toàn màn hình.

## 6. Theo dõi và xóa nội dung

- Màn hình được đánh dấu **Online** khi player gửi tín hiệu trong vòng 60 giây gần nhất.
- Xóa một màn hình sẽ xóa cấu hình playlist, nhưng không xóa các file khỏi kho nội dung.
- Xóa nội dung khỏi kho sẽ gỡ nội dung đó khỏi mọi playlist đang sử dụng. Hãy xác nhận trước khi xóa.

## 7. Khắc phục sự cố

**Không mở được trang quản trị**

- Kiểm tra ứng dụng còn chạy và mở đúng `http://localhost:3000/admin`.
- Nếu dùng máy khác, thay `localhost` bằng IP của máy chạy AdPlay.
- Kiểm tra firewall có cho phép kết nối đến máy chủ hay không.

**TV không mở được player hoặc không hiện Online**

- Đảm bảo TV và máy chủ cùng mạng LAN.
- Không dùng `localhost` trên TV; `localhost` sẽ trỏ về chính TV.
- Mở lại liên kết player ghép nối của màn hình.
- Nếu trình duyệt TV cũ, dùng liên kết **TV cũ**.

**Video tải xong nhưng vẫn đang xử lý**

- Chờ thêm; tối ưu video và tạo ảnh poster diễn ra sau khi tải lên.
- Nếu xử lý không thành công, ứng dụng vẫn có thể giữ và phát file gốc.

**Không có tiếng hoặc không vào toàn màn hình**

- Chạm vào màn hình hoặc bấm nút OK trên remote để cho phép phát âm thanh/toàn màn hình.

## 8. Bảo vệ và sao lưu dữ liệu

- Không giữ thông tin đăng nhập mặc định khi đưa ứng dụng lên mạng.
- Chỉ chia sẻ liên kết player với thiết bị cần phát; không công khai trang quản trị.
- Sao lưu định kỳ `backend/db.json` và thư mục `backend/uploads`. Hai vị trí này chứa cấu hình playlist, danh sách nội dung và file media.
- Nếu dùng dịch vụ host hoặc máy chủ khác, kiểm tra dung lượng lưu trữ và đảm bảo dữ liệu nằm trên ổ đĩa bền vững.
