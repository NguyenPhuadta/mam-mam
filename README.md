# măm măm. — Trưa nay ăn gì?

Web chọn món ăn trưa ngẫu nhiên, giao diện flat 2D tối giản với font Plus Jakarta Sans.

- Dải món chạy ngang, giảm tốc và dừng tại vạch giữa.
- Thêm, sửa, xoá mọi món ăn; hoàn tác lần xoá gần nhất.
- Lưu thực đơn và chế độ sáng/tối trên trình duyệt bằng localStorage.
- Tự nhận giao diện sáng/tối của hệ điều hành ở lần mở đầu tiên.
- Chặn tên món trùng; các món có xác suất được chọn bằng nhau.
- Hỗ trợ điện thoại, bàn phím và chế độ giảm chuyển động.

## Chạy

Mở `index.html` trực tiếp, hoặc chạy `python3 -m http.server 4173` rồi truy cập http://localhost:4173.

Font được tải từ Google Fonts; nếu không có mạng, trình duyệt dùng font sans-serif dự phòng.

## GitHub Pages

Trong Settings → Pages, chọn Deploy from a branch, nhánh `main`, thư mục `/ (root)` rồi Save.

Không cần cài thư viện hay build. Món tự thêm chỉ lưu trên trình duyệt đang dùng, không đồng bộ lên GitHub.
