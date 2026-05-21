# Skill 16 — CCCD & Address Parser

## Mục tiêu
Parse chuỗi địa chỉ Việt Nam thành dữ liệu có cấu trúc, giúp chuẩn hóa và tìm kiếm dễ hơn.

## Ứng dụng
- CRM
- ecommerce
- logistics
- form nhập địa chỉ
- Wikipedia
- dữ liệu hành chính

## Input ví dụ
```text
12 Nguyễn Huệ Quận 1 TPHCM
```

## Output mong muốn
```json
{
  "street": "12 Nguyễn Huệ",
  "district": "Quận 1",
  "city": "Thành phố Hồ Chí Minh"
}
```

## Chức năng chính
- tách số nhà, đường, phường, quận, tỉnh
- nhận diện alias
- chuẩn hóa viết tắt
- phát hiện địa danh cũ
- gợi ý sửa lỗi chính tả
- xuất JSON

## Dữ liệu xử lý
- địa chỉ đầy đủ
- địa chỉ thiếu thành phần
- địa chỉ viết tắt
- địa chỉ có lỗi dấu
- địa chỉ trộn tiếng Việt và tiếng Anh

## Luồng xử lý
1. Normalize khoảng trắng và dấu câu.
2. Chuẩn hóa alias như TPHCM, HN, Q1.
3. Nhận diện đơn vị hành chính.
4. Tách thành phần đường/phường/quận/tỉnh.
5. Gán độ tin cậy cho từng phần.

## Alias mẫu
- TPHCM → Thành phố Hồ Chí Minh
- HCM → Thành phố Hồ Chí Minh
- HN → Hà Nội
- Q1 → Quận 1
- Q.1 → Quận 1
- P. → Phường

## Edge cases
- địa chỉ thiếu số nhà
- địa chỉ chỉ có phường + quận
- địa chỉ quá ngắn
- nhiều địa danh trùng tên
- tên đường giống tên quận/huyện

## Pseudo-code
```text
normalize(text)
detect_aliases(text)
extract_parts(text)
score_confidence(parts)
return structured_address
```

## Output nên có
- `street`
- `ward`
- `district`
- `province`
- `confidence`
- `raw_input`

## Mở rộng nâng cao
- fuzzy matching
- geocoding
- kiểm tra trùng lặp khách hàng
- map sang chuẩn hành chính mới
- hỗ trợ OCR địa chỉ từ ảnh giấy tờ
