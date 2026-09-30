# măm măm. — Trưa nay ăn gì?

Web chọn món ăn trưa ngẫu nhiên, giao diện 2D màu pastel với font Plus Jakarta Sans.

- Dải món chạy ngang, giảm tốc và dừng tại vạch giữa.
- Thêm món mới và lưu trên trình duyệt bằng localStorage.
- Chặn tên món trùng; các món có xác suất được chọn bằng nhau.
- Hỗ trợ điện thoại, bàn phím và chế độ giảm chuyển động.

## Chạy

Mở `index.html` trực tiếp, hoặc chạy `python3 -m http.server 4173` rồi truy cập http://localhost:4173.

Font được tải từ Google Fonts; nếu không có mạng, trình duyệt dùng font sans-serif dự phòng.

## GitHub Pages

Trong Settings → Pages, chọn Deploy from a branch, nhánh `main`, thư mục `/ (root)` rồi Save.

Không cần cài thư viện hay build. Món tự thêm chỉ lưu trên trình duyệt đang dùng, không đồng bộ lên GitHub.
