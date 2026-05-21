# skill-convert-vietnam-address.md

# AI Skill — Chuyển đổi tỉnh thành cũ sang hệ thống hành chính mới

## Giới thiệu

Skill này dùng để:
- tự động chuyển đổi địa chỉ hành chính Việt Nam cũ
- chuẩn hóa dữ liệu tỉnh/thành sau sáp nhập
- hỗ trợ form nhập liệu
- hỗ trợ Wikipedia, CMS, ERP, CRM
- migrate database địa chỉ

Nguồn dữ liệu:
- https://provinces.open-api.vn/
- https://provinces.open-api.vn/api/v2/redoc

---

# Mục tiêu

Chuyển:
- tỉnh cũ
- huyện cũ
- xã/phường cũ

thành:
- tỉnh/thành mới
- xã/phường mới
- mã hành chính mới

---

# Ví dụ

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

---

# Tính năng

## 1. Normalize địa chỉ

Tự động:
- bỏ khoảng trắng thừa
- chuẩn hóa viết hoa
- sửa lỗi dấu tiếng Việt
- chuyển alias

Ví dụ:
- tphcm → Thành phố Hồ Chí Minh
- hn → Hà Nội

---

## 2. Convert đơn vị cũ → mới

Hỗ trợ:
- tỉnh cũ
- huyện cũ
- xã cũ
- phường cũ

Map sang:
- tỉnh mới
- phường/xã mới

---

## 3. Auto Suggest

Gợi ý khi nhập:
- tên tỉnh
- xã/phường
- autocomplete

---

## 4. API Integration

API chính:
https://provinces.open-api.vn/api/v2/

Swagger:
https://provinces.open-api.vn/api/v2/redoc

---

# Endpoint hữu ích

## Danh sách tỉnh

```http
GET /api/v2/p/
```

## Danh sách xã/phường

```http
GET /api/v2/w/
```

## Lấy thông tin tỉnh

```http
GET /api/v2/p/{code}
```

## Lấy thông tin xã

```http
GET /api/v2/w/{code}
```

---

# Flow hoạt động

```text
Input Address
    ↓
Normalize Text
    ↓
Lookup API
    ↓
Map Administrative Changes
    ↓
Generate New Address
    ↓
Return Result
```

---

# Ví dụ JavaScript

```js
async function getProvinces() {
  const res = await fetch(
    "https://provinces.open-api.vn/api/v2/p/"
  );

  const data = await res.json();
  console.log(data);
}
```

```js
async function getWard(code) {
  const res = await fetch(
    `https://provinces.open-api.vn/api/v2/w/${code}`
  );

  const data = await res.json();

  console.log(data);
}
```

---

# AI Prompt

```text
Bạn là AI chuyên chuẩn hóa địa chỉ hành chính Việt Nam.

Nhiệm vụ:
- nhận địa chỉ cũ
- chuẩn hóa dữ liệu
- chuyển sang hệ thống hành chính mới
- trả về JSON sạch

Luôn ưu tiên dữ liệu từ provinces.open-api.vn
```

---

# Use Case

- Wikipedia
- CRM
- ERP
- Ecommerce
- AI Agent
- Browser Extension

---

# Browser Extension Idea

## Stack
- React
- TypeScript
- Vite
- Chrome Extension API

---

# Tampermonkey

```js
// ==UserScript==
// @name         Vietnam Address Converter
// @match        *://*/*
// ==/UserScript==

(function () {
  console.log("Address Converter Loaded");
})();
```

---

# Kết luận

Skill này phù hợp để:
- cập nhật dữ liệu hành chính
- migrate hệ thống
- sửa nội dung Wikipedia
- chuẩn hóa địa chỉ Việt Nam
