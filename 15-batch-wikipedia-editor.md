# Skill 15 — Batch Wikipedia Editor

## Mục tiêu
Sửa hàng loạt nhiều trang Wikipedia bằng một quy tắc thống nhất, có kiểm soát và có khả năng hoàn tác.

## Khi nào dùng
- đổi tên địa danh hàng loạt
- sửa format chú thích trên nhiều bài
- cập nhật category
- thêm/đổi liên kết nội bộ
- chuẩn hóa văn bản theo bộ quy tắc
- thay từ cũ sang từ mới

## Rủi ro cần kiểm soát
Batch edit mạnh nhưng nguy hiểm, vì vậy phải có:
- chế độ xem trước
- log thay đổi
- giới hạn số bài
- backup
- khả năng revert

## Input
Có thể là:
- danh sách URL bài viết
- danh sách tiêu đề bài
- CSV
- JSON
- truy vấn Wikidata
- danh mục bài

## Output
- diff từng bài
- báo cáo bài thành công / thất bại
- thống kê số thay đổi
- file backup

## Luồng xử lý
1. Tải danh sách bài.
2. Lấy wikitext hiện tại.
3. Áp quy tắc thay đổi.
4. Sinh diff.
5. Cho người dùng duyệt.
6. Gửi edit nếu được chấp thuận.

## Ví dụ batch rule
- đổi “TPHCM” → “Thành phố Hồ Chí Minh”
- đổi category cũ → category mới
- thay `{{Chú thích web|url=...}}` theo format mới
- chuẩn hóa khoảng trắng
- sửa liên kết wiki sai

## CSV ví dụ
```csv
old,new
TPHCM,Thành phố Hồ Chí Minh
HN,Hà Nội
```

## Edge cases
- trang không có pattern cần đổi
- trang bị bảo vệ
- trang có nhiều template lồng nhau
- thay thế làm hỏng cú pháp wiki
- cùng một cụm xuất hiện nhiều ngữ cảnh khác nhau

## Pseudo-code
```text
for page in pages:
    text = fetch_wikitext(page)
    new_text = apply_rules(text)
    if new_text != text:
        show_diff(page, text, new_text)
```

## Safety
- luôn có dry-run
- chỉ sửa khi rule đủ chắc
- không batch nếu pattern mơ hồ
- không đè dữ liệu chưa kiểm tra

## Gợi ý công nghệ
- MediaWiki API
- Wikidata API
- Python script
- Node.js script
- bot framework
