# Skill 18 — Geo Coordinate Skill

## Mục tiêu
Biến địa chỉ thành tọa độ bản đồ và ngược lại để hỗ trợ bản đồ, infobox và dữ liệu địa lý.

## Tác dụng
- thêm tọa độ vào bài Wikipedia
- hiển thị bản đồ
- geocode địa chỉ
- reverse geocode từ tọa độ
- xác minh địa điểm

## Input ví dụ
```text
12 Nguyễn Huệ, Quận 1, Thành phố Hồ Chí Minh
```

## Output mong muốn
```json
{
  "lat": 10.7769,
  "lon": 106.7009
}
```

## Chức năng chính
- forward geocoding
- reverse geocoding
- chuẩn hóa kết quả
- xếp hạng độ tin cậy
- phát hiện địa danh mơ hồ

## Luồng xử lý
1. Nhận địa chỉ.
2. Normalize chuỗi.
3. Gọi API geocoding.
4. Chọn kết quả phù hợp nhất.
5. Trả tọa độ + confidence.

## Dữ liệu hỗ trợ
- tên đường
- phường
- quận
- tỉnh
- landmark
- tọa độ sơ bộ từ Wikidata

## Edge cases
- địa chỉ quá chung
- nhiều kết quả giống nhau
- địa danh đã đổi tên
- địa chỉ chỉ là một khu vực rộng
- tọa độ sai lệch do map provider

## Pseudo-code
```text
query = normalize_address(input)
results = geocode(query)
best = rank_results(results)
return best_coordinates(best)
```

## Output nên có
- `lat`
- `lon`
- `display_name`
- `confidence`
- `source`

## Gợi ý dùng nguồn
- Nominatim
- Wikidata
- Google Maps nếu hệ thống cho phép
- dữ liệu nội bộ

## Dùng trên Wikipedia
- infobox nhân vật
- infobox địa điểm
- bài công trình
- bài tổ chức có trụ sở rõ ràng
