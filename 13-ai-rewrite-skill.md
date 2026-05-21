# Skill 13 — AI Rewrite Skill

## Mục tiêu
Chuyển văn bản thường sang văn phong bách khoa, trung lập, phù hợp với Wikipedia. Skill này không được tự bịa thêm thông tin, chỉ được viết lại những gì đã có trong đầu vào hoặc dữ liệu đáng tin đi kèm.

## Khi nào cần
- bài viết quá quảng cáo
- câu văn quá cảm tính
- câu bị lặp
- đoạn dịch máy khó đọc
- nội dung dài cần gọn lại
- văn bản cần trung lập hóa trước khi đưa vào wiki

## Chức năng chính
- viết lại trung lập
- loại bỏ từ ngữ PR
- sửa ngữ pháp và dấu câu
- rút gọn câu dài
- giữ nguyên ý chính
- bảo toàn tên riêng và số liệu

## Input ví dụ
```text
Công ty ABC là doanh nghiệp hàng đầu, nổi bật với chất lượng vượt trội và dịch vụ đẳng cấp.
```

## Output mong muốn
```text
Công ty ABC là doanh nghiệp hoạt động trong lĩnh vực ...
```

## Nguyên tắc bắt buộc
- không thêm thông tin mới
- không phóng đại
- không dùng từ cảm xúc
- không dùng ngôn ngữ quảng cáo
- không thay đổi факт quan trọng
- nếu thiếu dữ kiện thì giữ nguyên hoặc đánh dấu cần bổ sung nguồn

## Luồng xử lý
1. Phân tích câu đầu vào.
2. Phát hiện từ ngữ mang tính quảng bá.
3. Giữ lại факт cốt lõi.
4. Viết lại theo văn phong bách khoa.
5. Kiểm tra xem có vô tình thêm thông tin mới hay không.

## Từ nên tránh
- hàng đầu
- xuất sắc
- nổi bật nhất
- đẳng cấp
- tuyệt vời
- duy nhất
- tiên phong nếu không có nguồn mạnh

## Từ thay thế an toàn
- hoạt động trong lĩnh vực
- được biết đến với
- theo nguồn
- được thành lập vào
- có trụ sở tại

## Edge cases
- đầu vào là bản dịch máy
- đầu vào có nhiều khẩu hiệu
- đầu vào có phần trích dẫn
- đầu vào chứa thông tin chưa kiểm chứng
- đầu vào quá ngắn, không đủ để viết lại

## Pseudo-code
```text
strip_marketing_words(text)
preserve_entities(text)
preserve_dates_numbers(text)
rewrite_neutrally(text)
return rewritten_text
```

## Prompt mẫu
```text
Viết lại đoạn sau theo văn phong trung lập kiểu Wikipedia.
Không thêm факт mới.
Giữ nguyên tên riêng, số liệu và mốc thời gian.
Loại bỏ quảng cáo, cảm tính và ngôn ngữ thổi phồng.
```

## Output quality checklist
- câu ngắn và rõ
- không thiên vị
- không quảng cáo
- có thể gắn nguồn được
- không làm sai nghĩa

## Mở rộng nâng cao
- rewrite theo từng mục
- rewrite giữ cấu trúc heading
- rewrite song ngữ
- rewrite theo mức độ trang trọng
- rewrite theo template bài wiki
