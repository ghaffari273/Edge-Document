# لیست دفترچه تلفن

این API امکان لیست کردن تمام دفترچه تلفن های مرتبط با حساب کاربری شما را می‌دهد.

## 📍 لینک دسترسی

```
POST {base_url}/api/phonebooks/list-new?page=1&per_page=10
```

## 🧾 هدرها

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📝 پارامترها

| پارامتر  | نوع     | الزامی | توضیحات                                            |
|----------|---------|--------|----------------------------------------------------|
| page     | integer | خیر    | شماره صفحه برای صفحه‌بندی (پیش‌فرض 1)              |
| per_page | integer | خیر    | تعداد مدخل‌ها در هر صفحه (پیش‌فرض 10، حداکثر 1000) |
| title    | string  | خیر    | فیلتر بر اساس عنوان دفترچه تلفن                    |
| id       | integer | خیر    | فیلتر بر اساس شناسه دفترچه تلفن                    |

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "id": 123654,
      "title": "تست",
      "count": 12,
      "export_status": 0,
      "import_status": 0,
      "created_at": "2025-01-19T12:26:25+00:00",
      "updated_at": "2025-03-11T13:38:08+00:00",
      "options": []
    },
    {
      "id": 838550,
      "title": "تست 2",
      "count": 1,
      "export_status": 0,
      "import_status": 0,
      "created_at": "2025-01-29T14:29:57+00:00",
      "updated_at": "2025-02-15T11:11:25+00:00",
      "options": [
        {
          "id": 1234,
          "title": "تاریخ تولد",
          "type": "date"
        }
      ]
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 6,
    "path": "{base_url}/api/phonebooks/listNew",
    "per_page": 2,
    "to": 2,
    "total": 11,
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
curl --location --globoff '{base_url}/api/phonebooks/list-new' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' '
```
