# ذخیره دفترچه تلفن
این API به شما امکان ایجاد یک مدخل جدید در دفترچه تلفن را می‌دهد.

## 📍 نقطه پایانی

```
POST {base_url}/api/phonebooks
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 بدنه درخواست

```json
{
  "title": "تست",
  "options": [
    "123",
    "456"
  ]
}
```

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                       |
| --------- | ---- |----------|-------------------------------------------------------------------|
| title     | string | بله      | عنوان مدخل دفترچه تلفن. حداکثر 200 کاراکتر.         |
| options   | array  | خیر       | آرایه‌ای از شناسه‌های گزینه‌ها که به مدخل دفترچه تلفن مرتبط می‌شوند. |


## ✅ پاسخ موفق

```json
{
  "data": {
    "id": 1234,
    "title": "تست",
    "count": "0",
    "export_status": null,
    "import_status": null,
    "created_at": "2024-08-12T08:52:17+00:00",
    "options": [
      {
        "id": 123,
        "title": "نام خانوادگی",
        "type": "string"
      },
      {
        "id": 456,
        "title": "نام",
        "type": "string"
      }
    ]
  },
  "meta": {
    "status": true,
    "message": "انجام شد",
    "message_code": "200-1"
  }
}
```

## ❌ پاسخ خطا — توکن نامعتبر یا منقضی (401)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "اطلاعات وارد شده صحیح نمی باشد",
    "message_parameters": [],
    "message_code": "400-1",
    "errors": {}
  }
}
```

## ❌ پاسخ خطا — درخواست نامعتبر (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "تکمیل گزینه عنوان الزامی است",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "title": [
        "تکمیل گزینه عنوان الزامی است"
      ]
    }
  }
}
```

## 🧪 مثال درخواست

```bash
curl --location '{base_url}/api/phonebooks' \
--header 'Authorization: Your Apikey/Token' \
--header 'Content-Type: application/json' \
--data '{
    "title": "تست",
    "options": [
        "123",
        "456"
    ]
}'
```
