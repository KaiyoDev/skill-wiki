# Skill 17 — Province Merge Mapper

## Mục tiêu
Chuyển địa chỉ hành chính cũ sang hệ thống mới sau khi có thay đổi, sáp nhập hoặc đổi tên đơn vị hành chính.

## Vai trò
Đây là skill rất quan trọng khi:
- migrate database cũ
- cập nhật hồ sơ
- chuẩn hóa địa chỉ trên Wikipedia
- xử lý dữ liệu nhập từ biểu mẫu cũ
- làm sạch dữ liệu doanh nghiệp

## Nguồn dữ liệu
- provinces.open-api.vn
- API tài liệu ở phần redoc
- mapping nội bộ nếu có lịch sử hành chính

## Input
```json
{
  "province": "Bình Dương",
  "district": "Dĩ An",
  "ward": "An Bình"
}
```

## Output
```json
{
  "province_new": "Thành phố Hồ Chí Minh",
  "ward_new": "An Bình",
  "normalized": "Phường An Bình, Thành phố Hồ Chí Minh"
}
```

## Chức năng chính
- map tên cũ sang tên mới
- map mã hành chính cũ sang mã mới
- gắn trạng thái merged / renamed / unchanged
- trả về địa chỉ chuẩn hóa
- lưu lịch sử chuyển đổi

## Luồng xử lý
1. Normalize địa danh.
2. Tra cứu theo tên và mã.
3. Xác định quan hệ cũ-mới.
4. Sinh địa chỉ mới.
5. Trả về kèm metadata.

## Output metadata nên có
```json
{
  "status": "merged",
  "old_code": "12345",
  "new_code": "67890",
  "confidence": 0.98
}
```

## Edge cases
- tên tỉnh bị nhập sai dấu
- địa chỉ có nhiều cấp không rõ
- thay đổi nhiều lần qua lịch sử
- dữ liệu cũ thiếu huyện
- ward trùng tên giữa các tỉnh

## Pseudo-code
```text
normalized = normalize_place_names(input)
match = lookup_admin_unit(normalized)
if match has new mapping:
    return map_to_new(match)
else:
    return fallback(normalized)
```

## Gợi ý triển khai
- cache mapping trong local DB
- cập nhật theo phiên bản dữ liệu mới
- có chế độ kiểm tra thủ công
- hỗ trợ batch migration

## Dùng trong Wikipedia
- sửa địa chỉ trụ sở
- cập nhật nơi sinh/quê quán
- chuẩn hóa thể loại địa phương
- sửa mô tả đơn vị hành chính
