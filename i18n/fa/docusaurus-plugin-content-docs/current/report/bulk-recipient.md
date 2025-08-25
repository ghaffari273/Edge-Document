# دریافت گیرندگان پیام

این API به شما امکان دریافت گیرندگان یک پیام ارسالی خاص با استفاده از شناسه آن را می‌دهد.

اگر وضعیت پیام نهایی شده باشد، وضعیت تحویل برای هر گیرنده نیز برگردانده خواهد شد.

## 📍 لینک دسترسی

```
GET {base_url}/api/report/recipients?page=1&per_page=10&bulk_id={messages_outbox_id}
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📝 پارامترها

| پارامتر  | نوع     | الزامی | توضیحات                                                     |
|----------|---------|--------|-------------------------------------------------------------|
| bulk_id  | string  | بله    | شناسه پیام ارسالی که میخواهید گیرندگان آن را دریافت نمایید. |
| page     | integer | خیر    | شماره صفحه برای صفحه‌بندی (پیش‌فرض ۱).                      |
| per_page | integer | خیر    | تعداد گیرندگان در هر صفحه (پیش‌فرض ۱۰).                     |

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "recipient": "+989190000000",
      "message": "متن پیام",
      "is_readable": true,
      "msg_parts": "1",
      "message_status": "1"
    },
    {
      "recipient": "+989120000000",
      "message": "با سلام",
      "is_readable": true,
      "msg_parts": "1",
      "message_status": "1"
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "path": "/api/report/recipients",
    "per_page": 10,
    "to": 2,
    "total": 2,
    "status": true,
    "message": "انجام شد",
    "message_code": "200-1"
  }
}
```

فیلد `message_status` می‌تواند یکی از مقادیر زیر را داشته باشد:

- `0`: ارسال شده به اپراتور
- `1`: اپراتور پیام را دریافت کرده
- `2`: پیام به گیرنده تحویل داده شده
- `3`: پیام به گیرنده تحویل داده نشده
- `4`: شماره در لیست سیاه

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
    "message": "تکمیل گزینه bulk_id الزامی است",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "bulk_id": [
        "تکمیل گزینه bulk_id الزامی است"
      ]
    }
  }
}
```

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/report/recipients?page=1&per_page=10&bulk_id={messages_outbox_id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' 
```
