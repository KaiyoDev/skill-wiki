# Skill 19 — Vietnamese Company Lookup

## Mục tiêu
Tra cứu và chuẩn hóa thông tin doanh nghiệp Việt Nam để hỗ trợ viết bài, kiểm tra dữ liệu và bổ sung nguồn tham khảo.

## Có thể tra gì
- tên doanh nghiệp
- mã số thuế
- địa chỉ
- ngành nghề
- người đại diện
- trạng thái hoạt động
- ngày thành lập

## Input ví dụ
```text
Công ty TNHH ABC
```

## Output mong muốn
```json
{
  "name": "Công ty TNHH ABC",
  "tax_code": "0xxxxxxx",
  "status": "active",
  "address": "..."
}
```

## Chức năng chính
- tìm doanh nghiệp theo tên
- xác minh mã số thuế
- chuẩn hóa tên pháp lý
- phát hiện trùng tên
- enrich dữ liệu bài viết

## Luồng xử lý
1. Nhận tên công ty hoặc MST.
2. Tra nguồn dữ liệu.
3. Chuẩn hóa kết quả.
4. Xác minh trùng lặp.
5. Trả về dữ liệu sạch.

## Output metadata nên có
- `legal_name`
- `trade_name`
- `tax_code`
- `address`
- `province`
- `status`
- `source`

## Edge cases
- công ty đổi tên
- công ty giải thể
- nhiều chi nhánh
- tên thương mại khác tên pháp lý
- dữ liệu viết tắt

## Pseudo-code
```text
query = normalize_company_name(input)
matches = search_company_registry(query)
best = rank_by_match_and_status(matches)
return normalized_company(best)
```

## Dùng trong Wikipedia
- viết bài doanh nghiệp
- cập nhật trụ sở
- chuẩn hóa mô tả
- xác minh độ nổi bật sơ bộ

## Lưu ý
- không dùng dữ liệu tự bịa
- không thay thế nguồn độc lập mạnh
- chỉ là lớp hỗ trợ tra cứu và chuẩn hóa
