# Skill 14 — Vandalism Detector

## Mục tiêu
Phát hiện sửa phá hoại, spam và nội dung không phù hợp trên Wikipedia để giảm thời gian tuần tra và giúp phát hiện sớm.

## Các dạng cần phát hiện
- spam quảng cáo
- chèn từ tục
- viết hoa toàn bộ
- thay thế hàng loạt bằng nội dung vô nghĩa
- xóa trắng bài
- chèn liên kết lạ
- thêm thông tin bịa
- lặp ký tự vô nghĩa
- sửa đổi có tính phá hoại rõ ràng

## Ví dụ phá hoại
```text
HAHAHAHAHAHA
```

```text
MUA NGAY GIÁ RẺ LIÊN HỆ 0912...
```

```text
abc abc abc abc abc
```

## Tín hiệu rủi ro
- quá nhiều chữ in hoa
- tỉ lệ ký tự lặp cao
- nhiều link ngoài bất thường
- thay đổi toàn bộ nội dung trong một lần sửa
- ngôn ngữ xúc phạm
- cụm từ spam quen thuộc
- edit có vẻ vô nghĩa so với ngữ cảnh

## Luồng xử lý
1. Lấy diff của lần sửa.
2. So sánh với phiên bản trước.
3. Chấm điểm rủi ro.
4. Gắn nhãn mức độ nghi ngờ.
5. Đề xuất revert hoặc kiểm tra thủ công.

## Output mong muốn
```json
{
  "risk_score": 0.91,
  "labels": ["spam", "caps", "nonsense"],
  "action": "review"
}
```

## Rule-based layer
- regex phát hiện URL spam
- regex phát hiện số điện thoại quảng cáo
- regex phát hiện từ khóa xúc phạm
- regex phát hiện ký tự lặp

## AI layer
- phát hiện văn cảnh phá hoại tinh vi
- nhận biết spam được viết lắt léo
- đánh giá mức độ bất thường của thay đổi

## Edge cases
- sửa lớn nhưng hợp lệ
- bài rất ngắn nên diff trông “to”
- bot sửa định kỳ
- nội dung trích dẫn hợp lệ nhưng có ngôn ngữ lạ
- phá hoại bằng cách thay một từ rất quan trọng

## Pseudo-code
```text
score = 0
if too_many_caps: score += 0.2
if spam_url: score += 0.3
if nonsense_text: score += 0.3
if large_unrelated_diff: score += 0.2
return clamp(score, 0, 1)
```

## Hành động gợi ý
- dưới 0.3: chấp nhận
- 0.3 đến 0.7: xem lại
- trên 0.7: nghi ngờ cao

## Mở rộng
- whitelist bot hợp lệ
- học từ lịch sử revert
- dashboard theo dõi trang bị phá hoại nhiều
- cảnh báo realtime
- tích hợp với chống spam community
