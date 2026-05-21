# Skill 12 — Quick Template Insert

## Mục tiêu
Tạo hệ thống chèn template Wikipedia thật nhanh bằng phím tắt, menu hoặc command palette. Skill này phù hợp cho người sửa wiki thường xuyên và hay dùng các mẫu lặp lại như chú thích, infobox, biển báo, chữ ký hoặc đoạn chuẩn hóa.

## Vấn đề cần giải quyết
Khi sửa Wikipedia, người dùng thường phải:
- gõ lại template dài nhiều lần
- nhớ cú pháp template
- copy/paste dễ sai tham số
- mất thời gian tìm đúng mẫu

Skill này biến mọi template phổ biến thành một thao tác rất ngắn.

## Chức năng chính
- gõ tắt để bung template
- danh sách template có thể tìm kiếm
- chèn theo vị trí con trỏ
- tự nhảy đến tham số đầu tiên cần điền
- hỗ trợ snippet theo ngữ cảnh bài
- đồng bộ snippet giữa nhiều máy

## Ví dụ phím tắt
- `;cw` → `{{Chú thích web}}`
- `;cb` → `{{Chú thích báo}}`
- `;xoa` → `{{Xóa}}`
- `;bio` → `{{Thông tin nhân vật}}`
- `;infobox` → `{{Infobox ...}}`

## Input
Người dùng nhập một mã snippet ngắn, hoặc chọn template từ UI.

```text
;cw
```

## Output mong muốn
```wiki
{{Chú thích web
|url=
|title=
|website=
|date=
|access-date=
}}
```

## Luồng xử lý
1. Nhận phím tắt hoặc tên template.
2. Tra bảng snippet.
3. Sinh đoạn wikitext.
4. Chèn vào vị trí hiện tại.
5. Đặt con trỏ vào ô đầu tiên cần nhập.

## Các loại template nên hỗ trợ
- chú thích nguồn
- thông tin nhân vật
- thông tin công ty
- bài viết sự kiện
- bản mẫu bảo trì
- bản mẫu dọn dẹp
- bản mẫu xóa
- bản mẫu dịch

## Edge cases
- template có nhiều dòng
- template có tham số tùy chọn
- template đã có nội dung cũ
- con trỏ đang nằm giữa đoạn văn
- người dùng chọn nhiều dòng trước khi chèn

## Pseudo-code
```text
IF shortcut exists:
    template = lookup(shortcut)
    insert(template)
    move_cursor_to_first_empty_field()
ELSE:
    show_template_picker()
```

## Gợi ý triển khai
### Tampermonkey
- chèn template trực tiếp trên trang sửa wiki
- bắt phím tắt
- hỗ trợ popup nhỏ

### VSCode snippet
- phù hợp nếu soạn wikitext offline

### AutoHotkey
- tốt cho thao tác nhanh toàn hệ thống

## Prompt mẫu cho AI hỗ trợ
```text
Hãy tạo template Wikipedia dạng wikitext.
Giữ đúng cú pháp.
Đặt các tham số quan trọng lên đầu.
Để trống các ô cần người dùng điền.
```

## Mở rộng nâng cao
- auto-gợi ý template theo loại bài
- detect article type từ tiêu đề
- chèn template tương ứng với danh mục
- lưu lịch sử snippet gần nhất
- import/export snippet bằng JSON

## Tiêu chí tốt
- chèn nhanh
- ít thao tác
- ít lỗi cú pháp
- dễ mở rộng
- phù hợp với nhiều loại bài
