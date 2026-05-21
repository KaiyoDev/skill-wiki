# Skill Wiki

`skill-wiki` là bộ tài liệu Markdown tiếng Việt dành cho việc biên soạn, rà soát và tự động hóa một số tác vụ liên quan đến Wikipedia tiếng Việt. Repo kết hợp hai nhóm nội dung chính:

- Quy định và hướng dẫn nền tảng khi sửa bài Wikipedia.
- Các ý tưởng skill/agent hỗ trợ chuẩn hóa dữ liệu, viết lại nội dung, phát hiện rủi ro và xử lý wikitext.

## Mục tiêu

- Tóm tắt các nguyên tắc cốt lõi của Wikipedia bằng ngôn ngữ dễ đọc.
- Làm checklist nhanh trước khi tạo, sửa hoặc rà soát bài viết.
- Chuẩn hóa các thao tác thường gặp như dẫn nguồn, viết trung lập, tránh quảng cáo và kiểm tra độ nổi bật.
- Ghi lại các skill có thể triển khai thành script, bot, browser extension, prompt hoặc workflow AI.

## Cấu trúc tài liệu

| File | Nội dung | Khi dùng |
| --- | --- | --- |
| [`00-README.md`](00-README.md) | Mục lục ngắn của bộ tài liệu | Đọc nhanh toàn bộ repo |
| [`01-nam-tru-cot.md`](01-nam-tru-cot.md) | Năm trụ cột của Wikipedia | Bắt đầu học cách sửa Wikipedia |
| [`02-trung-lap.md`](02-trung-lap.md) | Quan điểm trung lập | Viết hoặc sửa chủ đề có khả năng thiên lệch |
| [`03-kiem-chung-duoc.md`](03-kiem-chung-duoc.md) | Kiểm chứng được | Kiểm tra thông tin có nguồn đáng tin hay không |
| [`04-khong-nghien-cuu-chua-cong-bo.md`](04-khong-nghien-cuu-chua-cong-bo.md) | Không đăng nghiên cứu chưa công bố | Tránh tự suy luận, tự tổng hợp hoặc thêm kết luận mới |
| [`05-do-noi-bat.md`](05-do-noi-bat.md) | Độ nổi bật | Đánh giá một chủ thể có đủ điều kiện viết bài riêng |
| [`06-cam-nang-bien-soan.md`](06-cam-nang-bien-soan.md) | Cẩm nang biên soạn | Chuẩn hóa văn phong, bố cục và cách trình bày |
| [`07-quy-dinh-dat-ten-bai.md`](07-quy-dinh-dat-ten-bai.md) | Quy định đặt tên bài | Chọn tên bài ngắn gọn, phổ biến và chính xác |
| [`08-chu-thich-nguon-goc.md`](08-chu-thich-nguon-goc.md) | Chú thích nguồn gốc | Thêm nguồn, chú thích và thông tin xuất xứ |
| [`09-lien-ket-ngoai.md`](09-lien-ket-ngoai.md) | Liên kết ngoài | Quyết định link nào nên hoặc không nên đưa vào bài |
| [`10-khong-quang-cao.md`](10-khong-quang-cao.md) | Không quảng cáo | Nhận diện và sửa văn phong PR, marketing |
| [`11-skill-convert-vietnam-address.md`](11-skill-convert-vietnam-address.md) | Chuyển đổi địa chỉ hành chính Việt Nam | Chuẩn hóa tỉnh, huyện, xã/phường theo dữ liệu mới |
| [`12-quick-template-insert.md`](12-quick-template-insert.md) | Chèn nhanh template Wikipedia | Tạo snippet, phím tắt hoặc command palette cho wikitext |
| [`13-ai-rewrite-skill.md`](13-ai-rewrite-skill.md) | Viết lại bằng AI theo văn phong bách khoa | Trung lập hóa văn bản và loại bỏ ngôn ngữ quảng cáo |
| [`14-vandalism-detector.md`](14-vandalism-detector.md) | Phát hiện phá hoại | Chấm điểm rủi ro cho spam, xóa trắng, nội dung vô nghĩa |
| [`15-batch-wikipedia-editor.md`](15-batch-wikipedia-editor.md) | Sửa Wikipedia hàng loạt | Thiết kế batch edit có dry-run, diff, log và khả năng revert |
| [`16-cccd-address-parser.md`](16-cccd-address-parser.md) | Parse CCCD và địa chỉ | Tách địa chỉ Việt Nam thành dữ liệu có cấu trúc |
| [`17-province-merge-mapper.md`](17-province-merge-mapper.md) | Map đơn vị hành chính sau sáp nhập | Chuyển địa danh cũ sang địa danh mới kèm metadata |
| [`18-geo-coordinate-skill.md`](18-geo-coordinate-skill.md) | Chuyển địa chỉ thành tọa độ | Geocoding, reverse geocoding và hỗ trợ infobox địa lý |
| [`19-company-lookup.md`](19-company-lookup.md) | Tra cứu doanh nghiệp Việt Nam | Chuẩn hóa tên pháp lý, MST, địa chỉ, trạng thái hoạt động |
| [`20-ocr-to-wiki.md`](20-ocr-to-wiki.md) | OCR sang wikitext | Chuyển ảnh, scan hoặc PDF thành nội dung wiki sạch |

## Lộ trình đọc đề xuất

### Người mới sửa Wikipedia

1. Đọc [`01-nam-tru-cot.md`](01-nam-tru-cot.md) để nắm khung nguyên tắc.
2. Đọc [`02-trung-lap.md`](02-trung-lap.md), [`03-kiem-chung-duoc.md`](03-kiem-chung-duoc.md) và [`04-khong-nghien-cuu-chua-cong-bo.md`](04-khong-nghien-cuu-chua-cong-bo.md).
3. Trước khi tạo bài mới, đọc [`05-do-noi-bat.md`](05-do-noi-bat.md).
4. Khi biên tập nội dung, dùng [`06-cam-nang-bien-soan.md`](06-cam-nang-bien-soan.md), [`08-chu-thich-nguon-goc.md`](08-chu-thich-nguon-goc.md) và [`10-khong-quang-cao.md`](10-khong-quang-cao.md) làm checklist.

### Người xây workflow hoặc công cụ hỗ trợ

1. Dùng [`12-quick-template-insert.md`](12-quick-template-insert.md) để thiết kế snippet/template.
2. Dùng [`13-ai-rewrite-skill.md`](13-ai-rewrite-skill.md) để chuẩn hóa prompt viết lại nội dung.
3. Dùng [`14-vandalism-detector.md`](14-vandalism-detector.md) để thiết kế lớp phát hiện sửa phá hoại.
4. Dùng [`15-batch-wikipedia-editor.md`](15-batch-wikipedia-editor.md) nếu cần sửa hàng loạt, nhưng luôn bắt buộc có dry-run và review diff.

### Người xử lý dữ liệu Việt Nam

1. Dùng [`11-skill-convert-vietnam-address.md`](11-skill-convert-vietnam-address.md), [`16-cccd-address-parser.md`](16-cccd-address-parser.md) và [`17-province-merge-mapper.md`](17-province-merge-mapper.md) cho địa chỉ hành chính.
2. Dùng [`18-geo-coordinate-skill.md`](18-geo-coordinate-skill.md) khi cần tọa độ cho địa điểm, trụ sở hoặc infobox.
3. Dùng [`19-company-lookup.md`](19-company-lookup.md) để chuẩn hóa dữ liệu doanh nghiệp trước khi viết hoặc kiểm tra bài.
4. Dùng [`20-ocr-to-wiki.md`](20-ocr-to-wiki.md) để chuyển tài liệu giấy, ảnh hoặc PDF thành wikitext có thể chỉnh sửa.

## Nguyên tắc sử dụng

- Không tự thêm dữ kiện nếu không có nguồn đáng tin.
- Ưu tiên nguồn độc lập, có uy tín và có thể kiểm chứng.
- Viết bằng văn phong bách khoa: ngắn gọn, trung lập, không quảng cáo.
- Với chủ đề nhạy cảm, mô tả rõ ai nói gì và dựa trên nguồn nào.
- Với sửa đổi hàng loạt, luôn chạy thử, xem diff và giữ khả năng hoàn tác.

## Gợi ý triển khai thành công cụ

Các file skill trong repo có thể được chuyển thành:

- Prompt AI dùng trong trình soạn thảo.
- Script Python hoặc Node.js gọi MediaWiki API.
- Browser extension hoặc Tampermonkey userscript.
- VSCode snippet cho người soạn wikitext offline.
- Workflow kiểm tra bài trước khi xuất bản.

Khi triển khai tự động hóa, nên tách rõ ba bước:

1. Phân tích đầu vào và chuẩn hóa dữ liệu.
2. Sinh đề xuất hoặc diff thay đổi.
3. Yêu cầu người dùng duyệt trước khi ghi lên Wikipedia.

## Checklist nhanh trước khi lưu bài

- Chủ thể có đủ độ nổi bật không?
- Thông tin quan trọng đã có nguồn chưa?
- Nguồn có độc lập và đáng tin không?
- Câu văn có bị quảng cáo, cảm tính hoặc công kích không?
- Có dữ kiện nào là suy luận riêng hoặc nghiên cứu chưa công bố không?
- Template, chú thích, liên kết ngoài và tên bài có đúng ngữ cảnh không?
- Nếu là sửa hàng loạt, đã có dry-run, diff và log chưa?

## Giấy phép

Dự án sử dụng giấy phép MIT. Xem chi tiết tại [`LICENSE`](LICENSE).
