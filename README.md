# măm măm. — Trưa nay ăn gì?

[Chạy web](https://nguyenphuadta.github.io/mam-mam/). Giao diện flat 2D tối giản, font Plus Jakarta Sans; vòng quay ngang, thêm/sửa/xoá món, hoàn tác và dark mode.

Thực đơn dùng chung trên Firebase project `mamma-8ef91`, Cloud Firestore Standard tại Singapore. Mọi khách được đăng nhập ẩn danh tự động và đều có quyền sửa danh sách chung. Thay đổi hiển thị realtime ở các trình duyệt khác và vẫn còn sau khi tải lại trang. Theme và kết quả quay là riêng từng máy; thực đơn cũ trong localStorage không tự ghi đè thực đơn chung.

Mỗi lần sửa dùng transaction đọc bản mới nhất, kiểm tra tên trùng, rồi lưu nguyên tử. Giới hạn 1–40 món, tên tối đa 40 ký tự. Khi cùng sửa một món đã đổi tên, giao diện yêu cầu mở lại hộp sửa. Web chỉ xác nhận đã lưu sau khi máy chủ chấp nhận; mất mạng sẽ khoá sửa và cho kết nối lại.

## Chạy local

`python3 -m http.server 4173 --bind 127.0.0.1`, sau đó mở `http://127.0.0.1:4173/`. Không cần build; cần internet để tải Firebase SDK và đồng bộ.

## Backend

Bật Anonymous Authentication. Triển khai cấu hình với Firebase CLI: `firebase deploy --only auth,firestore --project mamma-8ef91`.

`menus/lunch` chứa danh sách, revision và server timestamp. Tám tài liệu `menuBlocks/0` đến `menuBlocks/7` chia phần kiểm tra schema thành khối tối đa 5 món để không vượt giới hạn biểu thức của rules. Cả chín tài liệu được ghi trong cùng transaction; rules yêu cầu revision và dữ liệu ghép khớp nhau. Chỉ khách đã đăng nhập được đọc/ghi đúng các đường dẫn này; xoá tài liệu và truy cập đường dẫn khác bị từ chối. Mỗi lần sửa ghi 9 tài liệu.

Security rules là bản đầu cho thực đơn công khai có mọi khách là người sửa. Rules kiểm tra schema, kích thước và revision; chống trùng tên/ID được kiểm tra trong transaction ở ứng dụng. Cần kiểm tra lại rules trước khi mở rộng quyền hoặc thêm dữ liệu riêng.
