# لیست شماره‌های دفترچه تلفن
این API به شما امکان دریافت فهرستی از تمام شماره‌های دفترچه تلفن را می‌دهد.

## 📍 نقطه پایانی

```
GET {base_url}/api/phonebooks/numbers/contact-list
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات |
| --------- | ---- |----------| ----------- |
| from_created_at   | string | خیر       | زمان برای فیلتر کردن شماره‌هایی که بعد از این تاریخ ایجاد شده‌اند. فرمت: Unix timestamp (ثانیه از epoch). |
| number            | string | خیر       | شماره تلفن برای فیلتر. فرمت: E.164 (مثال: +989121234568). |
| phonebook_title   | string | خیر       | عنوان دفترچه تلفن برای فیلتر. |
| phonebook_id      | string | خیر       | شناسه دفترچه تلفن برای فیلتر. |
| page      | integer | خیر       | شماره صفحه برای صفحه‌بندی (پیش‌فرض 1)               |
| per_page  | integer | خیر       | تعداد مدخل‌ها در هر صفحه (پیش‌فرض 10، حداکثر 1000) |

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "id": 1233,
      "phonebook_id": 123456,
      "pre": "",
      "name": "",
      "email": "",
      "number": "+989123456788",
      "created_at": "2025-04-19T11:11:41+00:00",
      "updated_at": "2025-04-19T11:12:51+00:00",
      "phonebook_title": "تست 3532"
    },
    {
      "id": 1234,
      "phonebook_id": 123456,
      "pre": "",
      "name": "",
      "email": "",
      "number": "+989123456789",
      "created_at": "2025-04-19T11:11:41+00:00",
      "updated_at": "2025-04-19T11:12:51+00:00",
      "phonebook_title": "تست 3532"
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "path": "{base_url}/api/phonebooks/numbers/contact-list",
    "per_page": 10,
    "to": 2,
    "total": 2,
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

## 🧪 مثال درخواست

```bash
curl --location '{base_url}/api/phonebooks/numbers/contact-list' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN'
```
