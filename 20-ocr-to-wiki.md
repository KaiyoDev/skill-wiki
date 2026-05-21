# Skill 20 — OCR to Wiki Skill

## Mục tiêu
Chuyển ảnh, scan, PDF hoặc tài liệu giấy thành nội dung wikitext sạch, có thể chỉnh sửa và bổ sung nguồn.

## Dùng khi
- có ảnh chụp bài báo
- có scan tài liệu
- có PDF cần trích text
- có ảnh chứa bảng dữ liệu
- có nội dung cần đưa vào wiki

## Pipeline
1. OCR ảnh hoặc PDF.
2. Tách văn bản.
3. Làm sạch lỗi OCR.
4. Nhận diện heading, bảng, danh sách.
5. Chuyển sang wikitext.
6. Gợi ý chú thích nguồn.

## Input ví dụ
- ảnh chụp báo
- PDF tài liệu
- scan sách

## Output mong muốn
```wiki
== Lịch sử ==
Nội dung đã được OCR và làm sạch.

== Nguồn ==
* {{Chú thích web|url=...}}
```

## Chức năng chính
- OCR đa ngôn ngữ
- sửa lỗi ký tự
- phục hồi xuống dòng
- nhận diện tiêu đề
- chuyển bảng sang wiki table
- trích link và nguồn

## Edge cases
- ảnh mờ
- chữ nghiêng
- nhiều cột
- bảng phức tạp
- footnote khó đọc
- file PDF scan kém chất lượng

## Pseudo-code
```text
text = ocr(file)
clean_text = cleanup_ocr(text)
structure = detect_headings_and_tables(clean_text)
wiki = convert_to_wikitext(structure)
return wiki
```

## Mở rộng
- OCR + translate
- OCR + citation extraction
- OCR + batch upload
- OCR + page diff
- OCR + source verification

## Tiêu chí chất lượng
- ít lỗi chính tả
- giữ đúng cấu trúc
- không mất nguồn
- dễ chỉnh sửa tay sau OCR
- không tự thêm факт mới
